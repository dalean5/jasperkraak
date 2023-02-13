---
title: 'Good Fun with Surface Pro3, Nested Hyper-V, Nano Server and Azure Site Recovery'
date: '2017-02-05T12:27:11-04:00'
author: jasper@kraak.com
tags:
    - MCT
    - 'Microsoft Azure'
    - 'Server 2016'
    - Surfcae
    - Azure
---

For a Microsoft event on Jamaica I was asked to deliver a session on Azure DR. I believe that seeing is believing so I always tend to use as little slides as possible and just demo the Solution. On a Saturday morning, I started out thinking and drawing out the Infrastructure I would need to pull that off.

I have a SOHO environment, and for Inova Solutions, my employer, I moved everything to the Microsoft Cloud. My Surface Pro3 (i5, 8 GB RAM) will just have to do as my “local datacenter”.

The steps for the Azure Site Recovery are very well explained here <https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-hyper-v-site-to-azure> including the screenshots so I will not copy that into this blog. For my “Onprem Datacenter I need a Hyper-V machine, well, Windows 10 has Hyper-V. Download the <span style="color:#222222">Azure Site Recovery Provider from the Azure Portal and run it. Bummer.  
</span>

![](http://www.kraak.com/wp-content/uploads/2017/02/020517_1626_GoodFunwith1.png)

Apparently, the installer does not see Hyper-V on Windows 10 as Valid to install the ASR Provider. I need a Server 2016 or Server 2012R2 Hyper-V. Lucky for me, both Windows10 Hyper-V and Server 2016 Hyper-V support Nested Hyper-V. To enable Nested Hyper-V you need to download and run a PowerShell script called <span style="font-family:Consolas; background-color:yellow">Enable-NestedVm.ps1</span> from <https://github.com/Microsoft/Virtualization-Documentation/tree/master/hyperv-tools/Nested> after which you can test by running <span style="font-family:Consolas
- background-color:yellow">Get-NestedVirtStatus.ps1</span> downloaded from the same repository. In the 1<sup>st</sup> script I had to confirm that I’d be running the Nested Hyper-V Server with less than 4 GB of memory.

![](http://www.kraak.com/wp-content/uploads/2017/02/020517_1626_GoodFunwith2.png)

My Nested Hyper-V Server running with 3 GB of memory I need to create some seriously small servers. And, another reason for creating small servers is that I want small disks to replicate. Thanks again Server 2016, we now have Nano Server! Here is a Quick Start Guide for Nano Server <https://technet.microsoft.com/en-us/windows-server-docs/get-started/nano-server-quick-start> . In no time, I created 2 Nano Servers, Nano1 and Nano 2, each assigned 128 MB of RAM and a 1 GB OS Disk. I successfully installed the ASR Provider and registered the Nested Hyper-V Server with the downloaded Registration file. Within 5 minutes my Server popped up in the Azure Portal and I could select my Nano1 and Nano2 Server to start replicating. And here they go:

![](http://www.kraak.com/wp-content/uploads/2017/02/020517_1626_GoodFunwith3.png)

And here they are:

![](http://www.kraak.com/wp-content/uploads/2017/02/020517_1626_GoodFunwith4.png)

I ran a Test Failover just to see if I could complete the whole exercise within 45 minutes, the length of my presentation. The test failover only took about 2 minutes.

![](http://www.kraak.com/wp-content/uploads/2017/02/020517_1626_GoodFunwith5.png)

 Just to demonstrate that with minimal equipment you can demo an Enterprise grade feature like Azure Site Recovery using some neat Technologies. The first build took a bit longer than 45 minutes to figure it all out. Ran the whole thing 3 times now to get comfortable with it doing it on stage, well within 45 minutes <span style="font-family:Wingdings">J</span>.

Happy demoing!!!
