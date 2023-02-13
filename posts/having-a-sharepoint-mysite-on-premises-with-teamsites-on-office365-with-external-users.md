---
title: 'Having a SharePoint MySite On Premises with Teamsites on Office365 with External Users'
date: '2011-10-10T12:46:16-04:00'
author: jasper@kraak.com
tags:
    - Uncategorized
---

So, I’m back! A great vacation and some very time consuming projects stood in the way of delivering some posts here.  
After all the Exchange stuff it’s time to move on to investigate SharePoint. I’ve been a SharePoint Fan for over 7 years now, mostly on back-end stuff. Now I turn more and more to the Collaboration features (on Office365 I can’t do no more back-ends :-)).

As with Exchange, let’s go Hybrid. Have the best of both worlds and migrate workloads at your own pace.

I sat down to do something with MySite, which is already in our on premises SharePoint 2010. Also, I’ve been doing some work on Extranet features on both our SharePoint 2007 (the Live ID solution) and our SharePoint 2010 using AD FS 2.0 for a customer. I want to move quickly from the Shared Teamsite to my MySite, that was my objective without RTFM (some colleagues will probably lynch me for that…).

So, for the MySite part, there is this option in the Admin Portal (or Central Administration if you want to do this the other way around) called “Trusted Site Locations”. But that has to be targeted to an Audience, bugger. I have found no way to trigger compilation of Audiences in the Admin Portal, so I just waited. I created a new Security in the Onprem AD, made myself a member of that group and forced the DirSync tool to get the Group available online. I created the Audience to use that Group and targeted the Trusted Site Location to the Audience. The Trusted Site location is, of course, the URL of my on premises MySite. Actually I did that twice, one more time in my “private” Office365. So now I work in 3 different SharePoint environments and use only one MySite (hey, I’m just ONE person). Pretty easy (except for the waiting part).

Inviting external people to the companies online SharePoint starts with going to the Admin Portal for SharePoint Online. There I prepped the whole environment for “Allow” invitations to external persons. Next step is to go into your Site and activate the feature within the Site Collection. Now you can invite External Users! Note: they can only Sign In using a Live ID or a (Identity Federated) Online ID. My test user (hey, it’s me in my private environment) received the invitation, click and go! To make it a bit less sloppy I created a SharePoint Group, made my test user a member of it and granted permissions to the Group. No so hard too!

The whole thing took me about half an hour (except for the audience compilation waiting).

Note: Just found out that Compiling Audiences happens only once a week, early Sunday Mornings. Lucky me, I started my tests on Saturday!
