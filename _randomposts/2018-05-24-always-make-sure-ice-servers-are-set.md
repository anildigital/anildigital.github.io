--- 
title: Always make sure ICE servers are set
layout: post
---

Recently I fixed a bug in a WebRTC based application I am working.

The problem was that. During the live WebRTC call when a user refreshed the page.. his stream was not getting published for other members. In WebRTC terms, for the peerConnection which did offer used to get an ICE failed event. 

While debugging code, I could not figure why only after refreshing the page, his browser's peerConnection got ICE failed event, and this issue didn't occur when he correctly joined the WebRTC call with the join button.

My application uses JavaScript to initiate WebRTC call. My application's code fetches ICE servers from a third party server with an HTTP call. So when a user manually pressed the join button, my JavaScript-based client followed the proper flow, it made an Ajax call to get ICE servers list from a third party server which returns the Twilio ICE Servers and then application initiated WebRTC call with these ICE servers in peerConnectionConfig.

So when this issue arrived? The issue was when user refreshed the page, WebRTC call used to get set up even before I get Ajax response to get ICE servers and set in peerConnectionConfig. Basically, ICE servers were set as empty in the peerConnnectionConfig when the WebRTC call was initiated. This was wrong. Successful WebRTC needs proper peerConnectionConfig.

So the situation was "It works on my machine" - When I tested WebRTC calls locally simulating multiple users by opening the app in multiple browser tabs, it always worked fine. This is because for two local browser windows/tabs… having ICE servers set as empty in peerConnnectonConfig is not an issue. Local calls don't need proper ICE servers as it is the same machine.

So the bug was occurring only when multiple computers with different networks. To establish a proper WebRTC connection.. correct ICE Servers needs to be set else.. ICE would fail.


### Wrong

![](https://i.imgur.com/3PFr5Qa.png)


### Right

![](https://i.imgur.com/sy6Kfxu.png)
