---
title: 'Attending Microsoft Management Summit 2013'
date: '2013-04-14T19:07:55-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - MCT
    - MMS2013
    - 'Server 2012'
---

On April 6 I will fly to Las Vegas where MMS2013 will start.

![](http://www.kraak.com/wp-content/uploads/2013/03/032213_1907_AttendingMi1.png)

I just finished building my Schedule and I will append my notes from each session into this Blog post.

Here’s my schedule:

- <span style="color: white
-">The Benefits and Reasons for Upgrading to Windows Server 2012 Active Directory  
    </span>
- <span style="color: white
-">Getting Started with Orchestrator and Service Manager  
    </span>
- <span style="color: white
-">System Center 2012 Configuration Manager SP1 Overview  
    </span>
- <span style="color: white
-">System Center 2012 SP1 Operations Manager Overview  
    </span>
- <span style="color: white
-">Getting Started with Windows Azure Virtual Machines and Virtual Networks  
    </span>
- <span style="color: white
-">How to Design and Configure Networking in VMM and Hyper-V  
    </span>
- <span style="color: white
-">Designing a Virtual Desktop Infrastructure Architecture for Scale and Performance  
    </span>
- <span style="color: white
-">Orchestrating Hyper-V Replica Planned Failover with System Center 2012 SP1  
    </span>
- <span style="color: white
-">Implementing Common Scenarios in Virtual Machine Manager: Services and Service Templates  
    </span>
- <span style="color: white
-">Cisco Virtual Networking Solutions for Microsoft Hyper-V Environments</span>
- <span style="color: white
-">Develop a Successful Flexible Desktop Strategy in Today’s Digital Era  
    </span>
- <span style="color: white
-">Monitoring and the Network and Storage Infrastructure with Operations Manager 2012  
    </span>
- <span style="color: white
-">Manage and Monitor Your Windows Azure Usage From System Center 2012 SP1  
    </span>
- <span style="color: white
-">How to Manage and Deploy Microsoft User Experience Virtualization Across an Enterprise  
    </span>
- <span style="color: white
-">Software Defined Networking with Windows Server 2012, System Center 2012 SP1  
    </span>
- <span style="color: white
-">Microsoft Application Virtualization 5.0: Migration and Coexistence  
    </span>
- <span style="color: white
-">Building the Perfect Windows 8 Image  
    </span>

<span style="color: white;">Now that I see it in all its glory it’s an impressive list, a lot of great work to do! Long days and short nights.  
</span>

So, it’s Friday night and I’m all set to go, my flight is tomorrow morning at 10 AM from Amsterdam. A 4 hour stopover in Philadelphia so I’ll be in Las Vegas around 9 PM Pacific Time.

That was a long trip, some 25 hours… Sunday morning I went of to Wallmart to buy me a bicycle for taking up up and down to the MMS2013 Venue; Manadalay Bay, which is some 5 miles from my hotel. For $ 95 I’m done, no cab fares for me (that’s what I thought).  
Going to Manadalay Bay I had a flat tire within 3 miles… bummer. A thorn is the backtire. I left my bicycle and continued walking. Got my MMS2013 Badge after walking The Strip up and down. And then I took a cab (poor excuse… blisters on my feet) back to the hotel and arranged to pick up my bike.  
Ok, Monday I’ll start posting teh Technical Stuff.

**MMS2013 KeyNote**

I attended quit a few keynotes over past 5 years at various Microsoft Conferences. In this MMS2013 Keynote one thing was really different: IT IS ALL HERE!

No promises of upcoming releases or beta demos. It’s all about what is available right now. Server 2012 with all its features in the middle, surrounded by System Center 2012 SP1, SQL 2012, Azure, Intune, Advisor, Office 365. So now is the time to automate all that stuff, leveraging all the features to enable businesses to do their business.  
I think of it as a very smart keynote: we have work to do NOW! Whether it is on premises or in a public cloud, probably a lot of bits of both for most enterprises. But with one and only one toolset and underlying technology: Microsoft.

**MMS2013 The Benefits and Reasons for Upgrading to Windows Server 2012 Active Directory**

This breakout sessions showed how easy it is to upgrade current domains to Server 2012, there is no reason not to. Domain Controllers become clonable on Hyper-V. Dynamic Access Control keeps data safe bases on multiple policies. Remote execution out of the box. Software controlled networking and Storage Spaces. Let’s go for it.

**MMS2013 System Center 2012 Configuration Manager SP1 Overview**

SCCM2012 has at least 2 highlights for me:  
1\. User-centric approach enables to give users the same experience on whatever device.  
2\. Integration with Intune meaning that we can manage devices without them connecting to the corporate network. Devices such as Windows RT, Windows Phone, iOS and Android!

**MMS2013 Private Cloud Reference Architectures**

This session was about all the work Microsoft and its Vendors have put into making things work. The biggest takeaway is that most of the things have already been done and are tested and documented. The trial and error method, as a lot of IT Pros use, is not going to do it when building Private Clouds. S you’d better use those Reference Architecture documents!

**MMS2013 Getting Started with Windows Azure Virtual Machines and Virtual Networks**

David Aiken turned out to be a very funny speaker and his session was great. He pretended to be a newbie and went through all the steps with all the questions while creating some VMs and connecting them. He concluded with: you do it once or twice like this and from then on you use Powershell!

**MMS2013 How to Design and Configure Networking in VMM and HyperV (Part 1 and 2)**

Wow, tough technical stuff at the end of the day: network virtualization or software based networking. You really need to switch some buttons in your brain to figure this out. Mainly it’s about 2 things:  
1\. Network Convergence: we can now put all network communications through just one NIC (teamed) instead of having separate NICs for different kind of communications. Less hardware, less cables!  
2\. Isolation: although we can use convergence we still can isolate VM Networks from each other. We can use the same (virtual) IP Ranges multiple times, tenants/customers can bring their own IP Ranges.  
A couple of advantages are that we can manipulate IP settings without configuring that on individual hosts or guests and that we can do Live Migrations across (physical) subnets.  
Don’t start with VMM and Clusters before you ingrained this stuff!

**MMS2013 Orchestrating Hyper-V Replica Planned Failover with System Center 2012 SP1**

Okay, you can initiate a planned replica failover from Hyper-V Manager manually. The @OrchestratorGuy took a different approach. From heavy touch, through lite touch, to zero touch. The principles of Orchestrator are simple
- it does nothing but it can do everything. So he assembled a couple of tiered runbooks to do the trick. Run the runbook and the failover occurs. Alsways nice to see such demo’s.  
Then he introduced System Center Service Manager into the game; initiate the failover through a Service Request in the Self Service Portal. Worked like a charm, with the CMDB being being updated, tickets opened and closed, properties of the VMs adjusted etc. etc. Great demo!  
The key point out of this session: before you can automate something, get your procedures straight!

**MMS2013 Implementing Common Scenarios in Virtual Machine Manager: Services and Service Templates**

The VM is not important, the Service is. So you should even use Service templates if the Service consists of only one V. It gives you more repeatability, consistency and ease of management. At first glance it looks somewhat overdone but when you think it through it’s quite logical if you are getting into automation.

**MMS2013 Develop a Successful Flexible Desktop Strategy in Today’s Digital Era**

I am a BIG fan of Eduardo Kassner. He was once again brilliant in his confronting sarcasm, I really like that. I am NOT saying anymore, here is the abstract, the video should be available tomorrow on Channel9.  
New desktop technologies such as BYOD, VDI, Slates, Consumerization, among other pressures are causing many IT environments to consider re-architecting their desktop infrastructure. In this session you will see predictions, market trends, and then proceed to separate myths from facts by proposing a mobile workspace strategy that focuses on meeting your users’ desktop requirements based on roles / personas, and enabling technologies rather than implying that one technology solution would fit all.

**MMS2013 How to Manage and Deploy Microsoft User Experience Virtualization Across an Enterprise**

UE-V is part of MDOP and it eases the pains of roaming profiles and combining profiles for desktops, laptops, remote desktops and VDI.  
UE-V does this in a smart way by using an agent on the client(s). The Agent captures the changes on either OS or Application level and stores them locally and on a Network Share when the reconfigures app is being closed or the OS being locked/logged off. Now the smart thing is that only the changes are uploaded and downloaded instead of the complete profile.  
There are no servers involved (except for the network share, which can be the AD-homedirectory), it also works offline, it is manageable through GPO and SCCM ant it comes with a bunch of out-of-the-box templates.  
It makes no sense not using this if you have MDOP!

**MMS2013 Automating System Center Deployment with the Powershell Deployment Toolkit**

Well, this was a really COOL session. The demo, started at beginning of the session, completed in 55 minutes and the System Center Suite was completely installed, including SQL, prerequisites, integration and Management consoles. Pffffff.  
They took a bit off effort to build this but then you have something. You only have to fill in some parameters such as server names, service accounts and stuff and the Powershell scripts do the rest, including the download of all necessary components!  
Awesome!

**MMS2013 Microsoft Application Virtualization 5.0: Migration and Coexistence**

I’m supposed to be an App-V specialist so this was a very interesting session. I’ve been doing stuff with App-V 5.0 but I did no go in yet to coexistence and upgrading. Now that I have seen the things mentioned in the abstract below, I see great opportunities at our customers!  
This session focuses on the process of migrating from App–V 4.6 to App–V 5.0, including coexistence of the App–V 4.6 Client and the App–V 5.0 Client.  
The process of migrating App–V 4.6 packages to App–V 5.0 will include using the App–V 5.0 Package Converter tool and the process of customizing converted packages to leverage App–V 5.0’s new features.  
We will also discuss some of the new features of the App–V 5.0 Sequencer that may make customers consider re–sequencing their applications instead of converting their App–V 4.6 packages

**MMS2013 Building the Perfect Windows 8 Image**

This session was almost a Hands On Instruction Lab, so I actually did the HOL after the session. An excellent session/HOL leveraging MDT and Windows8 for either Desktop Deployment or VDI Deployment.  
That concluded my MMS2013 participation.

General insights are mostly about automation and the roadmap towards that automation. I have a lot of stuff to share, why we should do those things and where to start.
