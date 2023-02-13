---
title: 'Office365 Hybrid Deployment Wizard with Exchange 2010 SP2'
date: '2011-12-05T21:02:34-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
---

Exchange 2010 SP2 is Here! Office365 Hybrid Deployment made easy? Let’s find out!

A while ago my local DataCenter crashed and so I had to rebuild my Office365 Demo environment. I was just about to configure the Hybrid Exchange, everything is ready for it…… so, I’m happy that Microsoft released SP2 today, December 5th, I’ll use the Wizard for that! This time I have a Backup ready and made some snapshots first.

Here’s the works:

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image002.jpg "image002")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image002.jpg)

After extracting the Service Pack and running setup

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image004.jpg "image004")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image004.jpg)

Prerequisites checker and “Upgrade”

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image006.jpg "image006")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image006.jpg)

Half an hour later….. not even a Reboot!

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image008.jpg "image008")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image008.jpg)

There is sits, New Hybrid Configuration, let’s hit it

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image012.jpg "image012")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image012.jpg)

Even the Federation Trust will be generated

Painless

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image014.jpg "image014")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image014.jpg)

Now manage this one

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image016.jpg "image016")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image016.jpg)

Oeps, something for ME to do too!

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image018.jpg "image018")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image018.jpg)

Been there, done that…

Gimme a T-Shirt

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image020.jpg "image020")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image020.jpg)

Second shot: hit it!

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image022.jpg "image022")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image022.jpg)

All prerequisites are in place

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image024.jpg "image024")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image024.jpg)

Fill out the Dialog Box

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image026.jpg "image026")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image026.jpg)

Select Accepted Domain (Mail Name Space)

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image028.jpg "image028")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image028.jpg)

I go to GoDaddy for this one and wait for 3 minutes….. then check the checkbox and click Next

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image030.jpg "image030")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image030.jpg)

Easy choices: I have only 1 Server……

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image032.jpg "image032")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image032.jpg)

Wow, out-of-the-box IPv6…..

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image0341.jpg "image034")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image0341.jpg)

IP + FQDN

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image036.jpg "image036")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image036.jpg)

Select Public (!) Certificate……

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image038.jpg "image038")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image038.jpg)

Here we go!

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image040.jpg "image040")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image040.jpg)

Oeps, let’s look into the Log files…..

We have an issue….. been there before:

INFO:Cmdlet: Enable-OrganizationCustomization

ERROR: System.Management.Automation.RemoteException: This operation is not available in current Service Offer

WTF?

<http://community.office365.com/en-us/f/162/t/5567.aspx> turns out that it’s something else….

ERROR: Subtask configure execution failed: Creating Organization Relationship

Hmmmm

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image042.jpg "image042")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image042.jpg)

No reboot after SP2 install? A reboot did the trick…… Success is here!

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image044.jpg "image044")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image044.jpg)[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image046.jpg "image046")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/image046.jpg)

All is looking very well indeed!

To be continued for all of the features…….

[Exchange 2010 SP2 is Here](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/12/exchange-2010-sp2-is-here.docx)

Click to download the Word Document!
