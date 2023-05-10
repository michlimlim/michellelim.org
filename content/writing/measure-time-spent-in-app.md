---
title: "How We Built Our Own Time-Tracking Algorithm for a Rust app"
date: 2023-05-09T22:37:35-04:00
description: "A technical blog post on how we built time-tracking for an app"
images: ["/images/time-spent/persistence-of-memory.jpeg"]
type: "post"
---

![Peristence of Memory by Dalí](/images/time-spent/persistence-of-memory.jpeg)

In 2021, I was working on a start-up that was building a desktop app. At one point, an investor asked us how much time users were spending in the app daily. Our existing optional telemetry couldn’t tell us. But we knew figuring it out would tell us if our app was useful.

Ideally, we would have reached for an off-the-shelf SDK from a telemetry provider to solve this for us. However, our app was written in Rust, whose package ecosystem is still developing. Our best shot would have been refactoring a Swift package for iOS to target Mac OS, but that would’ve added unnecessary complexity. We decided to write our own.

### Initial approaches

The naive implementation is to send heartbeat requests to the backend when the app is being used. However, it would’ve been too costly. We had to write data to our analytics service’s API, but the service charges by volume. The heartbeat solution would’ve generated too many events and eaten away our runway. We could’ve extended the heartbeat interval to decrease events but it would’ve cost us in accuracy. So we ditched the heartbeat solution. 

The next best idea would be logging an event when usage starts and another event when usage ends. We could log an event when the app is focused and another when the app is unfocused. But this overestimates usage because a user could leave an app focused overnight but not _use_ it. Moreover, this method is also sensitive to missing events: if the app crashes[^1] before the app is unfocused, we will lose track of that period of usage. 

### Sessionization

Instead, we can take advantage of usage events the client has already been sending to the analytics service. The idea is that we assume events happening within a window are part of the same session. Say we mark any two events that are less than 5 min apart as part of the same session. It would be reasonable to assume that the user is engaged with the app between those events. 

If an event does not happen within 5 min after the last event, we would consider that the session terminated.

![Event Sessionization](/images/time-spent/time-spent-event-sessionization.png)
_In this scenario, a client emits the events A, B, and C within 5 min of each other, and then emits Event D 6 min after. The first 3 actions are part of Session 1 which is the duration between A and C. And the last event is the start of a new session._

There are two scenarios where this approach can fail, but, in our case, they were deemed acceptable. 

On the one hand, a user who checks in on the app at least once every 5 min, but is switching between multiple apps would cause their time spent in the app to be overestimated. However, we are okay with this kind of error since the ultimate goal is to measure engagement, and a user who is checking in that often is clearly engaged for the entire duration, even if they are multitasking. 

On the flip side, if a user pauses to think for 6 min before clicking their next request-generating button, their actions would be counted as part of two separate sessions. The 6-min duration would not be counted as time spent using the app, even though the user was actively engaged the entire time. This could have been a real problem for us, but we found that in practice these kinds of pauses were rare.

### First attempt

We can tag on session information to each event. For each event, we tag it with the last session if it occurred within 5min of the last timestamp. We tag it with a new session timestamp otherwise.

{{< gist michlimlim 05a3cd1c10866d4d3c65d5f399853f3f >}}

### Second attempt

However, this approach under-recorded time spent since it did not account for **all** user activity. It only considered the activity of using flagship features, but did not account for regular user actions like typing or focusing the app.

We could send an event for each keystroke or window interaction, but this will flood our data warehouse. Instead, we decided to sample these events (let’s call them “App Active” events) at a coarser interval, e.g. 1min[^2]. 

We enqueued an App Active event to our telemetry queue only if the user performed any app active action within the last minute. We also merged redundant events: two consecutive App Active events in the same session gives us the same information as one. Similarly, an App Active event followed by a flagship usage event gives the same information as just the flagship usage event.

![Time spent queue](/images/time-spent/time-spent-queue.png)


Here’s how the code looked like:

{{< gist michlimlim 0456089d16859cacb5558ee328bff819 >}}



### Conclusion

Once we shipped this, we were able to visualize users’ time spent in the app[^3] with low event volume.

We found that our users use our app for a substantive part of their work days, and verified that our app was useful. 

![Time spent chart](/images/time-spent/time-spent-chart.png)


References:

[https://medium.com/analytics-and-data/effective-approaches-to-dealing-with-tracking-time-spent-on-content-and-webpages-695f63c02b8a](https://medium.com/analytics-and-data/effective-approaches-to-dealing-with-tracking-time-spent-on-content-and-webpages-695f63c02b8a)


<!-- Footnotes themselves at the bottom. -->
## Notes

[^1]:
     We could actually make this resilient to the app _closing_. We could write a SIGINT handler that saves the last recorded focus duration and sends it to the backend. However, we can’t do the same for app crashes, since a SIGKILL immediately terminates the app process.

[^2]:
     Because we built our own UI framework for the app, we were able to plug into the app’s input event handling logic to [keep track of the last action timestamp](https://gist.github.com/michlimlim/e0397ccd3993306b65dcdda431ffa267), and [sample this every 1 min](https://gist.github.com/michlimlim/b2ca54a281264067911ca1d6c6501c50). 

[^3]:
     Take every session and take the difference between the start time and last event of the session.
