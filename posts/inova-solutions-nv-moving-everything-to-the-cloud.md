---
title: 'Inova Solutions NV: Moving EVERYTHING to the Cloud'
date: '2013-11-02T01:16:09-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - Office365
    - 'Windows Azure'
---

A lot has happened since my last post. My wife and I moved to Aruba in The Caribbean and I found a great job as Solutions Architect for Inova Solutions NV. Inova Solutions NV is a Microsoft Gold Partner in Licensing, formerly known as LAR (Large Account Reseller), nowadays it’s called LSP (Licensing Solutions Provider). One of my roles is that of IT Manager for our own IT and that is what this blog is about.

As a true Caribbean Company we are scattered across a couple of islands: Aruba, Curacao, Trinidad &amp; Tobago and Jamaica and we have customers on those and a lot of other islands. The Network Infrastructure consists off some site-to-site VPNs and Client VPNs so we can reach our resources located on Curacao where ever we are.

The CEO had a goal for me to achieve by putting 50% of those resources in the Cloud by June 30<sup>th</sup> 2014. Soon I discovered that we actually only use applications that are available in the Microsoft Cloud already: Exchange, SharePoint, Lync and CRM. My goal now is to have all that migrated to the Online Services by the end of the year.

Plus some extra wins: we don’t really need Active Directory, authentication also goes to the Cloud. That means our PC’s and laptops can no longer be managed by AD and GPO’s. For that we will leverage Windows Intune. And finally we have this RDS Server that hosts 2 applications, neither of which relies on AD, we will just rebuild that RDS Server as VM on Windows Azure.

My Christmas wish list (here on Aruba you can already buy your Christmas stuff):

- Office365
- CRM Online
- Windows Intune
- Windows Azure AD
- Windows Azure Network
- Windows Azure VM

Sounds like we have a plan! By the 1<sup>st</sup> of January 2014 we can start decommissioning our whole Onprem Infrastructure, all the site-to-site VPNs and oh boy, all that Client VPN stuff (I do not understand that companies still deploy that, don’t we have DirectAccess at our disposal?).

The bet is on, I have 2 months from now to make it so.

Hopi Bon!
