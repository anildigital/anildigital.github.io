--- 
title: Always make sure ICE Servers are set
layout: post
---

Recently  I fixed a bug in my WebRTC based application.

The problem was that. during live call when a user refreshed the page.. his stream was not visible to other members (For his browser, it used to get `ICE failed` for his peerConnection)

I could not figure why only after refreshing the page, his browser got `ICE failed` event, not when he properly joined the call with button.

So here was an issue, my application uses JavaScript to initiate WebRTC call. When he manually presssed the join button, my JavaScript based client code, made an Ajax call to get ICE servers from a third party server which returns the Twilio ICE Servers and then I setup the WebRTC call.

Issue was, when user refreshed, WebRTC call used to get setup even before I get Ajax response to get ICE servers. Because of this ICE servers was set as empty for the call. This was wrong.

It works on my machine - When I tested locally, it always worked fine as for two local browser windows... having ICE servers set as empty is not an issue as you are connecting on the same machine.

Issue happens when you are using multiple computers with different networks. In order to establish a proper WebRTC connection.. correct ICE needs to be set else.. ICE would fail.


### Wrong

![](https://i.imgur.com/3PFr5Qa.png)


### Right

![](https://i.imgur.com/sy6Kfxu.png)
