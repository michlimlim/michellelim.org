---
title: "Stop just using “Frontend” or “Backend” to describe the Engineering you like"
date: 2020-09-13T12:44:00-04:00
description: "Why the “frontend” vs “backend” engineering axis doesn't map well to engineers’ psychology. And how using just one division can lead to job mismatches, turnover, and even push some new grad engineers into product management."
images:
  ["/images/fe-be-cover-photo.png"]
type: "post"
featured: true
---

**_Also posted on Medium [here](https://medium.com/@michlim97/stop-just-using-frontend-or-backend-to-describe-the-engineering-you-like-e8c392956ada)._**

![Stop Using Frontend Backend Cover Photo](/images/fe-be-cover-photo.png)

If there is one tip I could share with my fellow new engineers, it would be… Stop relying on the “Frontend/Backend” axis to understand the engineering you like. **The “Frontend/Backend” axis doesn’t map well to engineers’ motivations.** If you only use that axis, you can end up in projects you don’t like or worse still, give up on engineering prematurely. **Instead, try using the “Product/Infrastructure” axis as the first axis to understand your career preference.**

My goal is to share with you the language that could help you (and your manager) find your “sweet spot” engineering role. It took me a couple of bad internship placements and _pure luck_ to figure this out. So I hope that this essay saves some of you months of job mismatch. Shoutout to [Bolu ](https://twitter.com/bolu_ben)who after my [Tweet thread](https://twitter.com/michlimlim/status/1293336552832151559) on this thesis went viral on Tech Twitter, suggested that I turned the thread into an essay[^1].

**“Product/Infra” maps neatly to the psychology of how engineers pick projects and their motivations for learning to code.** Broadly speaking, there are 2 types of engineers[^2]:

1. “Product-first” engineers are obsessed with using code to solve a user problem and they see code as just a means to an end.

2. “Code-first” engineers are obsessed with the abstractions, architecture, tools and libraries in the code. Elegant code is the end.

Product-first engineers map to "Product engineering"—building, launching and maintaining features that solve user problems. They often love being in the same room as designers and product managers to learn about users, and they love finding technical opportunities that can improve the product.

Code-first engineers map to "Infrastructure engineering"—building infrastructure platforms that support applications, be it via building CI/CD pipelines, implementing logging, or supporting high traffic etc. They’re motivated to better the craft of programming and are often obsessed with things like test coverage, using the latest technologies, code architecture, etc.

(To be clear, there are “Product engineering” and “Infrastructure engineering” roles whether your users are external customers, third-party developers or internal consumers of an API[^3].)

Notice that both Product engineers and Infrastructure engineers touch the frontend and the backend. Many of them, especially product engineers, choose to specialize into frontend or backend as well. **The “Frontend/Backend” division is still a valuable axis.**

**However, using the “Frontend/Backend” in isolation of “Product/Infra” in project selection can lead to engineer-job Mismatch. Especially amongst Product engineers.** I am a Product engineer. When I tried out “Backend engineering” in an internship, I was assigned to an Infra role where day-to-day I migrated databases. I had joined the company because I wanted to work on their product. But I didn’t have the language to explain that to my recruiter. They conflated “Backend” with “Infra” and I ended up with a role too far from the user.

When I tried out “Frontend engineering” in another internship, I was assigned to a product close to the user. But the frontend engineers and I were left out of the meetings that discussed how the features would solve problems.

If you split your engineers by the type of technology they work on (i.e. “Frontend/Backend”), it is easy to assume that your Frontend engineers are happy to just work on translating finalized designs into UI/UX components. But if you split them based on their motivations (i.e.”Product/Infra”), you’d want to loop your Frontend product engineers into product discussions.

(The same engineer-job mismatch happens for Infra engineers too, but it is less prevalent because the “Frontend” and “Backend” labels usually only officially apply in Product engineering.)

Now, this next part may be a reach… but I think **many new grad Product engineers choose to be Product _Managers_** **because of this inadequate "Frontend/Backend" division**[^4]. Let’s jump back to my two internship examples. How would you feel if these were your only two internships over your college career? Given that you spent 12 weeks in each role, wouldn’t it be reasonable to conclude that those roles were mostly what “frontend” and “backend” were all about? Wouldn’t it be reasonable too to conclude that since you didn’t like both types of engineering, maybe engineering as a whole wasn’t for you? (And this self-dejection is especially easy to fall into if you are part of an underrepresented minority in engineering.) Why not be a _Product_ manager and solve user problems?

This scenario is very common. Engineering is esoteric. Even with an intern-team matching process, an Product engineering intern may not know that they should select Product engineering roles, let alone know which roles are Product engineering roles.

**But what if that same intern uses the “Product/Infra” language and advocates for a “Product Engineering” role?**

I was such an intern. I was so drained by my Infra role that I reached out to Product Managers in the company to enquire about their jobs. But then I advocated[^5] for a Product Engineering role and… my manager gave it to me. As a backend engineer on a product team, I worked with a team to [build the Video Newsfeed in Robinhood](https://techcrunch.com/2019/10/03/stock-trading-app-robinhood-revamps-its-newsfeed-with-the-wall-street-journal-and-ad-free-videos/). I built a large backend pipeline and also had the chance to engage with product questions regarding newsfeed ranking, video tagging, and user engagement. I spoke with engineering, data science, and business, balanced those interests, and wrote the resolution in code.

I found my sweet spot.

**At the end of the day, engineering is multifaceted and can be defined along more than one axis:** B2B vs. B2C, B2B top-down vs. B2B “bottom-up”, API-first vs. application-first, “Forward deployed” vs. “Software engineer”, etc. If we’re serious about making engineering accessible to all, we should champion any and all frameworks that can help new engineers find their sweet spot and be happy.

<!-- Footnotes themselves at the bottom. -->

### Notes

[^1]: I had met Bolu, a new grad in Bloomberg London, after he sent me a cold DM to thank me for the thread. He had sent my thread to his manager!!! It turned out that he had been struggling to express his project preferences to his manager, and the thread helped. The manager “got” it after reading the thread and now Bolu is on a product development team he is very excited about.
[^2]: I took the “code-first” vs. “product-first” engineer terminology from Xoogler Zach Lloyd’s blog: https://thezbook.com/
[^3]: Someone on Twitter (leon @lievetraz) replied with their attempt to classify internal tools teams into “Product/Infra” [here](https://twitter.com/lievetraz/status/1293555767430336518?s=20).
[^4]: There are hundreds of other reasons engineers choose to be PMs of course.
[^5]: I learned it the hard way how important it was to advocate for oneself and ask to change teams early.
