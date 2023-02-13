---
title: 'Azure in Plain Words'
date: '2014-12-12T10:59:47-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - 'Microsoft Azure'
---

![](http://www.kraak.com/wp-content/uploads/2014/12/121214_1459_AzureinPlai1.jpg)

Microsoft Azure is BOOMING. The platform is getting new features and feature updates on a daily basis and for most people it’s hard to keep up with that. Some may even give up on it, being overwhelmed by the possibilities on Azure. In this blogpost I will try to write in plain words on 8 features that I like most. No technical deep dives, just the functionalities and the benefits of having those functionalities running on Azure. Basically all sits in the cloud, meaning no local resources: Storage, CPU, RAM, and Networking. And you pay per use.

1. Azure Websites. Whatever website you want to run, a basis (static) public facing company website, a web application, a web shop, Azure offers the platform. This blog sits on Azure as simple Azure Website + WordPress template deployed on it. Takes about 10 minutes to set that up and have it running. For more complex web applications, with stuff running in a backend database, transaction processing we can deploy websites as Cloud Service. And finally, to have total control, we can create Virtual Machines running the web applications. All 3 options are scalable depending on demand and of course all 3 flavors come with their own set of benefits/drawbacks.![](http://www.kraak.com/wp-content/uploads/2014/12/121214_1459_AzureinPlai2.png)
2. Azure Virtual Machines. Within minutes we can spin on a Server and manage it as if it is spinning locally or we can upload Virtual Machines that are already running locally. Scale up the servers (add RAM and CPU) as needed or scale out (add servers) as needed. During the day time 6 servers could be running, at night there will be just one server running. Any Server Role can run on an Azure Virtual Machine. You could start with deploying a test &amp; development environment in Azure. In the template Gallery there are plenty of pre-loaded templates available:  
    ![](http://www.kraak.com/wp-content/uploads/2014/12/121214_1459_AzureinPlai4.png)![](http://www.kraak.com/wp-content/uploads/2014/12/121214_1459_AzureinPlai3.png)
3. Azure Virtual Networks. For those Virtual Machines to function they need to be placed in a network. We can create Virtual Networks on Azure to connect to those Virtual Machines and to connect the Virtual Machines to whatever they need to connect to. We can extend our local networks to Azure and spin on Servers and Services as needed.
4. Azure Service Bus. More and more applications tend to communicate with each other. In order to do that there must be some kind of communication infrastructure in place. Through Azure Service Bus applications can talk to each other wherever the application runs. Some applications just talk while others only listen and some may do both, so that those distributed applications can complete the tasks they are set up to do.
5. ![](http://www.kraak.com/wp-content/uploads/2014/12/121214_1459_AzureinPlai5.png)Azure Remote App. Azure Remote App became General Available just a week ago and enables organizations to publish just about any application to end users wherever they are. Scalable, resilient, redundant and connected to any backend required. Remote App has been available running on onprem servers for a couple of years, this takes it to the cloud!

![](http://www.kraak.com/wp-content/uploads/2014/12/121214_1459_AzureinPlai6.png)

1. Azure Storage. Of course Services we run on Azure require storage. Fast storage, high available storage, cheap storage. One of the use cases for Azure Storage is backup of local servers. We all know that backups should be kept off premises, well, this is a nice way of having that in place.
2. Azure SQL Database. A lot of applications need a SQL Database to store, query and retrieve data. And sometimes it’s a bit over the top to go to a full-featured SQL Server. Azure SQL Databases offers SQL Database services without the need of deploying a Virtual Server and install SQL Server on it. ![](http://www.kraak.com/wp-content/uploads/2014/12/121214_1459_AzureinPlai7.png)
3. Azure Active Directory. Authentication and Authorization mechanisms need to be out there in order to allow users to access the resources in Azure. We can integrate that with our local Active Directory but also with “industry authentication providers” like Google and Facebook through Azure Access Control Services.

Microsoft Azure offers more than mentioned in this blogpost, please visit <http://azure.microsoft.com/> for more information.
