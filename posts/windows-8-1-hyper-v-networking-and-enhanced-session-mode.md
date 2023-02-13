---
title: 'Windows 8.1 Hyper-V Networking and Enhanced Session Mode'
date: '2014-06-24T09:55:14-04:00'
author: jasper@kraak.com
tags:
    - 'Computers and Internet'
    - Office365
    - 'Server 2012'
    - Windows8
---

As a good Administrator should, I have two user accounts. One as an ordinary user and one Admin Account. We have all our Services running in the Microsoft Cloud and of course I do not want to fill out my credentials every time I open my browser or do stuff in Private Browser sessions. Although tearing it down, we still have some servers Onprem and to access those I need a VPN Connection to our Cisco ASA appliance (I live on Aruba and our office sits on Curacao). It took me some trial and error to get things going…… with my Virtual Admin Machine.

@Home I have a simple Wi-Fi set up and as we all know by now, running a Virtual Admin Machine just over a Wireless Network Adapter is no great success. The proper way to set that up is as follows:

In Hyper-V Manager, create a new Internal Switch:

 ![](http://www.kraak.com/wp-content/uploads/2014/06/062414_1354_Windows81Hy1.png)

Assign the Network Adapter of the VM to that Internal Switch:

![](http://www.kraak.com/wp-content/uploads/2014/06/062414_1354_Windows81Hy2.png)

Go to Network and Sharing center on the Host, click properties on the Wireless Adapter and hit the Sharing Tab and share it with the Internal Switch:

![](http://www.kraak.com/wp-content/uploads/2014/06/062414_1354_Windows81Hy3.png)

At this point the Cisco AnyConnect Secure Mobility Client (3.1) on the Host refuses to connect over the Wi-Fi connection because the adapter is being shared. Bummer. There is probably a workaround for that but I want my Admin stuff not on the Host but on the VM. So this is just a note.

I installed the Cisco AnyConnect Secure Mobility client in the VM and tried to connect. Bummer……. The client refuses to connect out of a RDP Session. I used my favorite Search Engine:

- There is a client config file on the local machine -&gt
- not so
- In the ASDM Console connected to the Cisco ASA Appliance there is Node called “Client Profile Settings -&gt
- not so
- Both the ASDM Console and the ASA OS are outdated, downloading the latest version -&gt
- Both the ASDM Console and the ASA OS are outdated, downloading the latest version -&gt (Cisco) accountname + pw -&gt
- not documented…..

So, I tried starting at the other end, the VM. How come “RDP”? Am I not connected to the Console in the “Virtual Machine Connection”? My favorite Search Engine again: A “cool” feature of Windows 8.1 Hyper-V is “Enhanced Session Mode”. By default this is set to “Enabled”. It allows for RDP-like experience in the Virtual Machine, redirection of drives etc. There are three places where you should look:

![](http://www.kraak.com/wp-content/uploads/2014/06/062414_1354_Windows81Hy4.png)

![](http://www.kraak.com/wp-content/uploads/2014/06/062414_1354_Windows81Hy5.png)

And in the Virtual Machine Connection Window:

![](http://www.kraak.com/wp-content/uploads/2014/06/062414_1354_Windows81Hy6.png)

Unchecking the “Enhanced Session” in the Virtual Machine Connection did the trick. The Cisco AnyConnect Secure Mobility Client now connects through my Shared Wi-Fi Connection!

All in a days work………
