---
title: 'Exchange 2013 Hybrid Deployment on Office365 leveraging Azure'
date: '2012-10-15T20:48:43-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - Office365
    - 'Server 2012'
    - 'Windows Azure'
---

With all the new releases of Servers, Services and Devices, I thought it was time to build a Hybrid Deployment using Exchange 2013 Preview and Office 365 Preview.

I set out to do everything on Server 2012 but unfortunately that didn’t work out. So I had to cheat a little (making it more interesting though); my <span style="text-decoration: underline
-">**onprem**</span> environment consists of Server 2012 machines only. The Win2k8R2 machine I needed runs on Azure. The AD FS Service required for Single Sign On with Office 365 does not (yet) run on Server 2012. As the High Available AD FS Service is a constraint for a lot of customers to go for SSO, this might be good option anyway. Have your AD FS Servers in the Cloud, you could even force geo-redundancy and stuff like that.

So, I first need to acknowledge Office 365 MVP Jethro Seghers (<http://jethroseghers.blogspot.nl/> and @jsegehrs) from Belgium who already set up this config but has had no time yet to describe it.

Secondly I used a great blogpost from Paul Cunningham on installing Exchange 2013 on Server 2012 (<http://exchangeserverpro.com/install-exchange-2013-pre-requisites-windows-server-2012> .

And Trevor Smith for getting DirSync to run on Server 2012 <http://community.office365.com/en-us/forums/613/p/63806/243279.aspx>

I also acknowledge myself <span style="font-family: Wingdings
-">J</span> for my earlier posts on setting up a Hybrid Deployment (been there, done that, got the certifcations….. no t-shirts though).

Okay, that being said, let’s get going.

Here is my Bill of Materials:

- Office 365 Preview Tenant, get it at <http://www.microsoft.com/office/preview/en>
- Windows Azure Preview Account, get it at <http://www.windowsazure.com/en-us/>
- Exchange 2013 Customer Preview, get it at <http://www.microsoft.com/exchange/en-us/exchange-preview.aspx>
- At least 2 Server 2012 instances in your local environment (3 would be better)
- Public domain namespace, I use GoDaddy for that
- Public Certificate, either wildcard (for non-production) or SAN-Certificate (I use a ucc-GoDaddy, requested through Exchange and added domain name for my AD FS Instance)
- AD FS 2.0 Setup binaries, get it at <http://www.microsoft.com/en-us/download/details.aspx?id=10909>
- Microsoft Online Services Module for Windows PowerShell, get it at <https://portal.microsoftonline.com/IdentityFederation/IdentityFederation.aspx>
- Directory Synchronization tool, get it at <https://portal.microsoftonline.com/IdentityFederation/IdentityFederation.aspx>

And you need a couple of rainy Sunday afternoons to set it all up. It’s not that hard but we all met Mr.Murphy, he’ll check in every now and then.

<span style="text-decoration: underline
-">**Onprem Configuration**</span>

I have a lack of resources so I only used 3 VMs in my “Private Cloud”: a Domain Controller, an Exchange Server and a Windows 8 client. It’s certainly no best-practice to put the Directory Synchronization tool on the Exchange server but it works.

It’s all straight forward configuration work, the certificate tool in Exchange 2013 works great. Just make the request, go to your certificate provider to submit the request and import the certificate. This is what it looks like:

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2011.png)

I added the “sts” so I can use this certificate on the AD FS Server as well.

Create some users, dynamic distribution groups and mailboxes and start mailing, scheduling and stuff like that. There should be something in there before we start moving things to Office 365.

Then you do **ALL** of the tests in the Exchange Remote Connectivity Analyser (<https://www.testexchangeconnectivity.com/> ):

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2012.png)

….. and fix any issue before proceeding (keeps Mr.Murphy away).

<span style="text-decoration: underline
-">**Azure Configuration**</span>

The new Azure Portal is a real pleasure to work with, everything is in the place where you expect it to be. First we have to do some networking so that the VMs running on Azure can connect to the Onprem environment, using also your Onprem DNS Server. On Azure you have to create a so called Gateway Network and private subnet, name them as an Affinity group. Tick the Checkbox that you want to use this Gateway Network to connect to you Onprem environment.

Azure gives you the Gateway IP Address and there’s a button that will show the Pre-Shared Key to use when setting up your IPSec LAN-to-LAN VPN Tunnel. On my Draytek Router (running from my HAN, Home Area Network) that was a quick one. Although the default time-out was too low (300 sec), I adjusted it to 1500 secs. The result (in the pic even my two VMs are already spinning):

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2013.png)

I set up 2 VMs on Azure, just pick them form the Gallery, I took a Server 2012 for a Read-Only-Domain-Controller (it only serves authentication purposes out there) and a Win2k8R2SP1 for the AD FS Server. When the Networks are properly configured the machines obtain the appropriate IP Addresses. A RDP Endpoint is automatically created so you can manage the machines through RDP. I created an additional Endpoint for the AD FS Service.

I did the dcpromo wizard to create the RODC (the Azure Neworking gave it the right IP settings, including my Onprem DNS Server) and I also joined the AD FS Server to the domain.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2014.png)

<span style="text-decoration: underline
-">**Office 365 Preview Configuration**</span>

The steps to take in the Admin Portal are the same as they are in the current version, it is still very important (keeps you out of trouble) to do thing in the right order.

So, assuming that all is set to go, working and tested, this is the order:

- Set up Single Sign On by installing AD FS 2.0 and configure it with the proper commandlets in de MSOLPowershell Module.
- The previous step asks that you must add a TXT Record in DNS for validation, after doing that you re-issue the last commandlet
- Verify the addition of your domainname in the Portal
- Enable Directory Synchronization, it’s just a button in the Portal. It says it might take 24 hours, my experience is it takes about 30 minutes.
- When you see that DirSync is enabled you can run the configwizard prompting for both Online Admin credentials and Onprem (Schema) Admin credentials
- Verify Directory Synchronization in the Portal, your Onprem AD Users should be listed there
- Verify SSO by logging in to the Portal with a Synchronized user

All this is necessary because a Hybrid Exchange Deployment uses only Federated Users, thus AD FS and DirSync.

<span style="text-decoration: underline
-">**Exchange 2013 and Exchange Online Hybrid Deployment**</span>

Finally, we’re getting there. Getting the 2 Exchange Organizations talk to each other, allowing for Calendar Sharing, mailbox moves, complete GALs , etc, etc. I was not that enthusiastic about the wizard in Exchange 2010 SP2. It takes away the deeper level insights of what is actually happening. In my Trainings I still do it the manual way and if time permits I let my students do the SP2-Wizard.

So I’m quit curious about the Exchange 2013 “Exchange Administration Center” and the Wizard in there…..

As soon as you hit “Hybrid” in the al new Exchange Admin Center, a button appears with “Enable”, then it asks you to logon to Exchange Online so you end up in the Exchange Admin Center …… online! As soon as you hit Hybrid in there, a button appears with “Enable”. Looks like that way you have enabled Hybrid Deployment on both sides.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2015.png)

That looks very promising! YES! The next one looks familiar from the “old” Hybrid Deployment, proof of ownership for your domain:

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2016.png)

I go to GoDaddy to do just that. Oeps, slight error in the “Copy to clipboard”, it also takes the domain name field… do NOT put that into your DNS Tool!! GoDaddy is fast, I could continue right away.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2017.png)

Centralized Mail Transport allows for mail flow from Exchange Online to the Internet to be routed through your Onprem mail servers (Compliance, Journaling or whatsoever). The Edge Role does not exist anymore (as TMG will soon) so I choose Hub Transport.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2018.png)

Easy choice, I only have one server deployed…. It should be an Internet facing CAS Server though, Hybrid Deployment is leveraged by Exchange Web Services found through Autodiscover. I skip the next screenshot, it’s the same but now it’s about the Sending Server.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange2019.png)

I have set up my Exchange Certificate real good! Exchange Online recognizes it right away. And asks me for the SMTP Address of my Onprem server:

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20110.png)

No surprise here (I’ll keep that for myself <span style="font-family: Wingdings
-">J</span>):

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20111.png)

This looks almost too easy to be true:

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20112.png)

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20113.png)

Checking Onprem, checking Tenant, checking prerequisites ….. a

All the manual steps from the good old times come by….. and yes indeed, this used to be the case all the time….

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20114.png)

It used to be a matter of time-outs, so I’ll just cancel it (changes made are already there) and do some manual stuff, but not after running the wizard for a third time (Mr.Murphy please leave).

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20115.png)

Let’s see what there is to modify….. hmmm, not much, exactly the same Wizard with the same results <span style="font-family: Wingdings
-">L</span>.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20116.png)

Hey, I’m on Wave 15! This appears when I look at the Node “Organization”.

Here’s the FIX!

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20117.png)

I added my namespace not from the Online Interface but from the Onprem Interface! That seems to be working perfectly! Just passed all the nodes and settings and it looks okay…. Time to move a Mailbox to Online, I guess.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20118.png)

The usual credential stuff (I’m triggering the Move from Online):

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20119.png)

The Wizard does it wrong again…. As in Exchange 2010 SP2, the automatically configured endpoint is my local FQDN, which is of course not resolvable from Online. I manually enter the webmail.domain.domain endpoint and of we go.

![](http://www.kraak.com/wp-content/uploads/2012/10/101512_1848_Exchange20120.png)

YES! There he is! Note the very, very, very small arrow pointing to “Office365”, took me some minutes <span style="font-family: Wingdings
-">J</span>, by that time the move had already completed (just 2 items).

Last checks for now:

- mailflow Onprem-Online and vice versa check
- mailflow Online-Internet and vice versa check
- Calender sharing check
- That all will double check the AD FS Deployment as well <span style="font-family: Wingdings
-">J</span> check

Great!

Been there, done that, now I want the T-Shirt!

Thanks for reading and don’t hesitate to comment or to contact me!
