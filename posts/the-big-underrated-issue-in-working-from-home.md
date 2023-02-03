---
title: 'The Big Underrated Issue in Working from Home'
date: '2020-05-12T08:00:33-04:00'
author: jasper@kraak.com
tags:
    - '#wfh'
    - 'Cloud Computing'
    - 'Computers and Internet'
    - COVID-19
    - Productivity
---

Although the initial anxiety on COVID-19 has dropped by now, lots of Organizations are aware that Remote Work is here to stay. And we see lots of applicable Technologies that can facilitate that. But mostly just up to the point where we come to “Line of Business Applications” (LOBs).

Most of my Customers have a pretty traditional setup of their IT Infrastructure in a on premises data center. Active Directory, member Servers running (legacy) client/server applications in sometimes a 2-tier infrastructure. The Local Area Network (LAN) sits in the Corporate Building and all Desktops have connectivity to the local data center. Some of these Customers started with moving some workloads to the Cloud, mainly email that goes to Office 365. Adoption and moving more workloads or starting to use new things in the Office 365 platform is going very slow.

And now we need to work remote. Outside of the Corporate LAN. That poses several challenges. For the sake of the topic I refrain from looking at processes relying on physical paper although a lot of my Customers still do so. Of course, that makes the challenge of working remotely even more complex.

<span style="text-decoration:underline">**The Devices** </span>

In most Office buildings people have a Desktop, I think in most cases, even in this COVID-19 situation, people are not allowed to take that one home. And even if they are allowed, it will not be connected to the Corporate LAN, so work as usual is not an option. Also, things like Group Policies (including Security settings) will not be applied to those Desktops. Corporate laptops suffer the same unless they are decently prepared for remote work. Lots of people will work on their personal device from home, or even their family device, Organizations have to realize that those devices are totally out of control. Then, users will use anything trying to accomplish their tasks using any application they can find. That list is endless by now and 99% of it fits in the category of “Shadow IT”, corporate data can and will flow anywhere.

<span style="text-decoration:underline">**Business Applications** </span>

Organizations can use a lot of different applications throughout their companies, per department or division. Some of them will just be a standalone application, a lot of them will tie back into a backend in the datacenter. Are these Line of Business Applications accessible for Remote Workers? Can they be made accessible, in a secure and user-friendly way? Some protocols to connect to these backends are not that suitable to traverse Wide Area Network (WAN) connections, resulting in a bad user experience or very limited functionality. Some Organizations already have some of their Applications accessible from outside the Corporate LAN
- email is probably the most common one.

In general, a Client device must be fully managed and sit as close to the Data Centre as possible, preferably over Corporate LAN Connections. Add to that, a decent Data Protection configuration. That is the ideal situation. Or is it?

There are numerous options to make LOB Applications accessible for use outside of the Corporate LAN, and they all have their pros and cons.

- VPN into the Corporate LAN
- applications may seem very unresponsive/low performance, a simple thing like browsing a File Server is hard over a VPN connection. Can the VPN-appliance on the Corporate LAN side and the Internet connection handle the load? Are the remote devices secure? Can the “client” side of the LOB Application be installed on the Remote Device?
- DirectAccess. Only available for Windows 10 Enterprise domain member PC’s. Transparent end-user experience (Always on), very secure (IPSec), Certificate based authentication, fully managed PC through GPO. Can the Corporate LAN side appliance and the Internet connection handle the load?
- Web-based applications. These are relatively easy to expose and authenticate to. The http(s) protocol is designed for WAN Connections.
- Re-architect application to Web-bases applications.
- Remote Desktop Services. The actual (virtual) Desktop runs within the Corporate LAN. Modern RDP Protocols (or the proprietary Citrix and VMware ones) are designed for WAN Connections. RDS or VDI Services are expensive, they require large amounts of resources: CPU, RAM, Storage, Networking. It also requires Infrastructure specialists and Application packaging specialists. Managing and maintaining a SBC environment requires a lot of IT Staff resources.
- Move LOB Applications to the Cloud. Make them available and accessible from anywhere. For “legacy” applications there is still the issue about the distance between the client and the server though.
- Move LOB Applications to the Cloud AND build SBC in the Cloud like Windows Virtual Desktop (WVD). WVD is not cheap (resource intensive) and almost just as hard to manage and maintain as an on-premises SBC Solution.
- All the above scenarios leave the end user device as is, unmanaged and not secure (except for Direct Access). With Microsoft 365 (Office 365, EMS, Intune) we can manage any device (Windows, MacOS, iOS, Android), implement things like Multi Factor Authentication, Conditional Access, Information Protection, Threat Protection, and lots of telemetry to analyze that all. The Office 365 portion allows for Communication and Collaboration (Email, Teams, SharePoint). Implementing Microsoft 365 will make all of the above scenarios easier and more secure.

What we can see happening right now is a myriad of all these options, which is fine as long as there is a Strategy or Vision stating where it leads to. If a Strategy is lacking all we are left with is a pile of unmanageable “spaghetti”. In the meantime, all scenarios could be valid under some specific circumstances. There is not one right way of doing it.

My “prefect picture” would look like “All Applications deployed in the Cloud, preferably as SaaS or PaaS Solution. All Devices managed through M365”.