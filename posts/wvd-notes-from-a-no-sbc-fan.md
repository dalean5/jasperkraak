---
title: 'WVD Notes from a NO-SBC fan'
date: '2020-05-19T08:27:02-04:00'
author: jasper@kraak.com
tags:
    - '#wfh'
    - 'Cloud Computing'
    - Productivity
    - WVD
---

People who know me also know that I am no fan at all about Server Based Computing (SBC). Remote Desktop Services, Citrix, VMware, VDI, WVD, it is all the same complex and expensive misery to allow Organizations to keep on running their legacy Win32 Line of Business Applications.

This racket of mine is not new. Back in 2007 I joined a Dutch company called Qwise, and Qwise was one of the major players in The Netherlands on Citrix and App Packaging and deployment. I asked myself and my colleagues: Why do we do this? Why don’t we make all applications web-based? Who needs a Desktop, who needs an OS? Because Organizations run shitty Line of Business Applications.

Now we are 2020 and nothing has changed. SBC is still expensive and it is still very complex (also in the Cloud) because Organizations still run shitty applications…..

Okay, anyways, I have been doing some playing around with Windows Virtual Desktop as a Pilot in our production environment. It took me like a day or two to get it all up and running thanks to this [article by Christiaan Brinkhoff](https://www.christiaanbrinkhoff.com/2020/05/01/windows-virtual-desktop-technical-2020-spring-update-arm-based-model-deployment-walkthrough/) . It is great that Microsoft will now manage the RDS Roles in the background. That surely takes away some headaches. And of course, provisioning on Azure is fast. Currently I do all of my daily job in a Virtual Desktop except for Teams Meetings. Pretty happy with the fluency and the performance. I oversized the VM’s a bit, I have to admit, but no fancy GPU stuff. I am waiting for the A/V Redirect to make Teams Meetings working.

There are quit some hoops to jump through setting this all up. I wonder how that is for less experienced people, there is much to deal with. My 70+ Microsoft Certs are well spent on this endeavor . Inova Solutions, the Company I work for, is a “Cloud Only” Company. I abolished all on-prem stuff, got rid of Active Directory, all happens from the Cloud and in the Cloud. The biggest “bummer” of WVD is that it relies on Active Directory. So, either put up some DC’s in Azure or deploy Azure Active Directory Domain Services. Back to Active Directory feels like “legacy” after doing only Azure AD and Intune for the last 6 years. Back to NTLM Authentication and GPO’s. I consider that a huge step back.

We also need to manage, one way or another, the end user device to enable these users to connect to their WVD environment including local printers, scanners and other devices, secure Corporate data, etc. WVD is not replacing those devices, WVD adds another Device per user, adding work to IT Staff to manage and maintain the complete environment.

In my [previous Blog](https://www.kraak.com/?p=2857) I wrote about connecting to (legacy) Line of Business applications for Remote Work. Not much to be found on “best practices” for WVD and those LOB Apps availability.

I can see valid use cases for WVD but maybe not so much for SMB unless they are served by a Managed Service Provider, the SMB’s in my customer base simply do not have the Knowledge for WVD. The Total Cost of Ownership for WVD, as it becomes so clear with the monthly bill from Microsoft for Azure consumption, may be considered high, I tend to look at the Value more than at the Cost. Valid Business cases can be written for deployment of WVD.

Anyways, I’ll keep on experimenting, trying and find valid scenarios for #WVD