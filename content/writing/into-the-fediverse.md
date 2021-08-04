---
title: "Into the Fediverse"
date: 2021-06-26T23:10:43-04:00
description: "Social media apps should share the same social graph by implementing ActivityPub"
images:
  ["https://s3.amazonaws.com/www.michellelim.org/images/anti-facebook.png"]
type: "post"
---
## Social media apps should share the same social graph by implementing ActivityPub
![A web consisting of Poparazzai, Dispo, Clubhouse, Snapchat, and Houseparty](https://s3.amazonaws.com/www.michellelim.org/images/anti-facebook.png)

#### Dear social media app startups,

I love joining new social apps! Last month, I signed up for Poparazzi as soon as it dropped. I was all for it! You could only post photos of others and not yourself? Sounds like a good antithesis to Instagram’s overcuration! I added contacts. I reacted to my friends' Pop’s. I Pop’ed a friend.

And then I stopped using it. 

It joined a host of other great apps—Dispo, Clubhouse, House Party, etc. All at one point promising to challenge Facebook’s Hegemony. All now deleted. What happened? 

I believe new social apps’ growth stagnates because they don’t enjoy the network effects of Facebook. (I know this is not an original take.) However, I also believe you can circumvent this problem by implementing [ActivityPub.](https://www.w3.org/TR/activitypub/) It’s a decentralized social networking protocol standardized by the W3C. It allows you to tap into the networks of users from other apps that also implement the protocol. The user retention and discoverability benefits you’ll gain from the shared social graph just might outweigh the concerns around moat.


### The Club of Abandoned Social Apps

Back to the great apps that I have uninstalled. I stopped using them because I couldn’t find enough friends there. It wasn’t meaningful to post about a friend when they weren’t on the platform. It was less rewarding knowing that few of our mutuals would see it. **[Even with all the hype it gathered](https://techcrunch.com/2021/05/26/poparazzi-hypes-itself-to-the-top-of-the-app-store/), Poparazzi couldn’t match Facebook’s Network Effects.** Let’s not even talk about social apps that never made it to public awareness.

Moreover, my brain didn’t have the capacity for yet another social app. The burnout from keeping up with multiple apps is real—it’s the reason that people are begging for [a messaging solution that integrates messages from multiple social platforms](https://www.texts.com). **If we could easily support integrated feeds, trying out a new app transforms from a daily intention to a single-installation action.**


### My Proposal: Share the Social Graph

I think these retention problems are solved if your users could interact with each other across apps. Make use of the same social graph.

It’s like E-mail. We take it for granted that any email user can send and receive emails from anyone else with an email address. That’s because their various servers (e.g. Outlook and Gmail) implement SMTP. They are built in different ways and have different properties (e.g. spam filters) but they are all compatible at the protocol layer.

Why can’t social media behave the same  way? ActivityPub (along with Matrix) is the most popular open social network protocol.  I use [Mastodon](https://joinmastodon.org/)—the ActivityPub version of Twitter. And within it, I can follow any user from PeerTube—the ActivityPub version of Youtube. Here’s what PeerTube posts look like on my Mastodon feed.

![Screenshot of me viewing PeerTube from Mastodon](https://s3.amazonaws.com/www.michellelim.org/images/mastodon-screenshot.png)

### The business case for a shared social graph

Facebook is never going to fully release their social graph. Right now if your app uses the Facebook Graph API, you can only see a user’s friends if they too install your app. It benefits Facebook to set constraints. And nothing’s stopping them from removing their Graph API completely.

On their own, new social apps and your walled gardens can’t rival the big forest that is Facebook; but combining your growth efforts onto a large enough social graph just might. Consumers may not have the headspace to download a host of new apps, but they’d be willing to download **one** app that gave them access to social media innovations.

In a world where all new apps implement ActivityPub, **users are more likely to stick to your new apps.**



1. When I try posting from a Hot New App, I can now tag existing friends; my rewards for posting are high too, since I know my friends can see my posts.
2. It’s also easier for me to keep up with content from the Hot New App. From my current app I’m used to, I just follow the users from the Hot New App. I can interact with their posts daily without having to visit a separate app. 

You also get **discoverability and virality benefits out of the box.** Your new social app’s users can now be followed and “retweeted” across their friends in all other networks. If they like the content, you’d create accounts on your app. This is the kind of **organic growth** that companies heavily rely on—remember Andreesen Horowitz pushing Clubhouse content all over your Twitter feeds last year?

In fact, the only truly successful new social media app in the last decade has been TikTok and it was in part due to the aggressive crossposting of TikTok videos onto other platforms. What if that crossposting were automatic?

 

And **all these benefits come with relatively low engineering overhead.** No need to chase down each app and integrate with them. You just have to handle a few GET and POST request endpoints. 

To allow users outside your app to direct-message users on your app, your server would have to accept the following JSON object as a POST request from other apps. Your client would then retrieve it to display it.
![JSON of DM](https://s3.amazonaws.com/www.michellelim.org/images/alyssa-dm.png)
[Example 3 from ActivityPub specs](https://www.w3.org/TR/activitypub/#Overview)

Here, Alyssa from Social App has sent a personal message to Ben from Chatty app. The fields are straight-forward: recipient, sender, note.

If she wanted to post that to her servers, her server would set the `to` field to `"https://social.example/alyssa/followers/"`. If she wanted to post a different content type, her server could extend the object. For example, this is an `object` that’s a Markdown:

![JSON of Markdown](https://s3.amazonaws.com/www.michellelim.org/images/alyssa-markdown.png)
[Example 8 from ActivityPub specs](https://www.w3.org/TR/activitypub/#obj-id)

### Into the Fediverse

The tradeoff of adopting a shared open standard? You might lose your network moat.

But what’s the point of a network moat if it’s not big enough? SnapChat’s Stories idea was great but consumers preferred using the same feature on their much larger Instagram network. I don’t think consumers would’ve switched to Instagram if most of their network was already on Snap. You can build up moats in other ways, such as in building superior models of social media—be it in content type, curation, discovery, fact verification, or moderation.

Fighting a monopoly will require collective power. The Fediverse offers a way for social apps to band together to have a shot at winning. Shoutout to the ActivityPub team and all early adopters for showing us a way to build a world like this.
\
\
**Yours sincerely,**\
Michelle\
Your huge fan
