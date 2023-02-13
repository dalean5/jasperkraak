---
title: 'Building Rich Coexistence on Office365 Beta, Part I'
date: '2011-03-09T19:43:50-04:00'
author: jasper@kraak.com
tags:
    - Office365
---

**[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/03/logo-office-365.png?w=150 "logo-office-365")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/03/logo-office-365.png)**Building Rich Coexistence on Office365 Beta, Part I****

Shortly after visisting the Office365 Ignite Session in Dublin (Feb.2011) I finally got my beta-account for Office365. As a BPOS Trainer/Consultant I was really looking forward to the Enterprise Features in Office365. So I ran into building one of the more complex scenario’s on Office365, Rich Coexistence for Exchange.

Rich coexistence is considered to be a long term relationship between Exchange On premises and Exchange Online and it should make no difference in the user experience whether their mailbox is locally hosted or in the cloud.  
Roadmaps are not easily found, I just took the Lab Manual from the Ignite Sessions and went along. And while doing this, the steps are not so hard to get. So here they come:

1. Build and AD Domain, a server running Exchange 2010 SP1 (don’t be too hasty in applying Rollup 2, you might need to unistall that one), a server prepared for installing ADFederation Services 2.0 (can be your DC, a server (x86) for installing the Directory Synchronization Tool.
2. Choose a nice Public Domain Name, Register it somewhere, get a wildcard certificate.
3. Make sure your Domain is mailable in your Exchange deployment, inbound, outbound, OWA, Outlook Anywhere, Unified Messaging. The works.
4. Set domain users to logon through a UPN with the domainsuffix of your public domain.
5. Add your Custom/Vanity domain to your Office365 account, either through the Portal or through the tool delivered with the ADFSconfig.msi. You will need access to your public DNS settings to verify ownership of the domain namespace.
6. Setup the Directory Synchronization server and Synchronize. Verify the synchronized users in the Portal
7. Assign licenses to the users.
8. Install ADFS 2.0.
9. Install the wilcard certificate (re-keyed for the IIS Instance on that server), in IIS.
10. Configure Identity Federation with the adfsconfig.msi delivered powershell commands.  
    Verify configuration in the ADFS Management Console.
11. Verify Identity Federation by logging on to the Portal with your UPN, you will not be promted for a password but redirected to your ADFS Server.

So, that was the easy part, that’s why it is called Part I. In a couple of days I will layout the Exchange Federation.  
If you do not have a beta-account yet, sign-up for one! In the meanwhile set up your test environment and make it work.  
Have Fun!
