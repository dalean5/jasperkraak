---
title: 'Office 365 Hybrid with Exchange 2007 &#038; Exchange 2013: Trouble!'
date: '2013-12-02T21:17:54-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - 'Exchange 2007'
    - 'Exchange 2013'
    - Office365
---

Currently I’m working on an Office365 Migration. Although the end goal is to have all resources Online, I always prefer to do the Hybrid Deployment. The best and only reason for that is that this has the least impact on end users. And that is what it’s all about: keep the customer satisfied.

First I cleaned up the 5 year old mail environment. Old mailboxes from long gone users, weird aliases, shared mailboxes and distribution lists. Exchange 2007 ran SP1 CU8 and that was not enough to introduce Exchange 2013 in the Exchange Organization. Moved it up to Exchange 2007 SP3 CU11. Cool.

Secondly I installed AD FS and DirSync, which are both required for Hybrid Exchange deployments. As I plan to have the whole migration done over the weekend, I did not do a fully redundant AD FS installation; just one server. Oh, I updated the SAN Certificate with “sts” and “legacy”, so I’m done with only the one certificate that was already on the Exchange 2007 box. Added my mail namespace to Office365 and ran **ALL** the tests with the Remote Connectivity Analyzer <https://testconnectivity.microsoft.com/> (never leave home without it).

Thirdly I did all the prerequisites for installing Exchange 2013 CU3, also, cool. Things were looking real good, services kept running and no user impact whatsoever. OWA, ActiveSync, Outlook, OAB, everything smiles here on Aruba (the servers are actually located on Curacao). And I ran **ALL** the tests with the Remote Connectivity Analyzer. I decided to do the mailbox moves prior to the switch of the MX Record and the autodiscover record.

Finally home, I launched the Hybrid Configuration Wizard in the Exchange Admin Center. All looks well, next, next, finish, no errors. Cool stuff, that Wizard. I’m from the old school, when Office 365 just launched, some years ago, I did the whole configuration of Federated Exchange manually. I am sure glad I did that a couple of times and as a Trainer I have seen participant make all the possible mistakes. So I know about mailflow, certificates, TLS, smarthosts, accepted and authoritative domains. Because it is getting ugly, real ugly now.

I created a test account Onprem and moved it to Online, which went okay. But no mailflow….. no mailflow from Onprem to Online ……. no mailflow from Online to Onprem….. no mailflow from External through Onprem to Online…… yeah, mailflow from Online to External. That is a 25% score; NOT GOOD. Big Trouble, a NO-GO for migrating users at this stage.

Troubleshooting. Message Tracking, Delivery Reports. After some hours of configuring and reconfiguring, rerunning the Hybrid Exchange Wizard, NDR’s showed up that servers would keep trying to send the messages: *“451 5.7.3 STARTTLS is required to send mail”.* That one I brought to my favorite Search Engine (<span style="text-decoration:underline">**B**</span>ut <span style="text-decoration:underline">**I**</span>t’s <span style="text-decoration:underline">**N**</span>ot <span style="text-decoration:underline">**G**</span>oogle) and a big list of articles appeared. Let’s have a read. The outcome is that I disabled the created Send Connector on my Onprem Exchange 2007 Server (apparently that server did not even recognize the connector cause on editing the config it sputtered “cannot find object on DC01). And I created a new one and set it to use TLS for my online namespace. Ah, some mailflow! From Onprem to Online is working! So the Online Inbound Connector is okay! So, we’re up to a 75% score! Getting better. The Online Outbound Connector is faulty (at least with an Exchange 2007 Onprem Server). I disabled it, created a new one going to “Partner” instead of “Onprem”, Opportunistic TLS and the namespace of my Internet Domain. And we’re up to 100% Mailflow!!!!

Maybe I should have set all the incoming and outgoing mailflows to the Hybrid Exchange 2013 server to avoid all this, but I didn’t. Therefore my conclusion is that the Hybrid Configuration Wizard does NOT work with an Onprem Exchange 2007 Server because Exchange 2007 Server does not know what the difference is between “Partner” and “Onprem” and it also does not recognize the Send Connector created by the Wizard.

So now I can sit on my porch on One Happy Island Aruba and be satisfied with the results. Next weekend I migrate mailboxes, now I start studying for my SharePoint 2013 Exam.
