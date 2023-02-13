---
title: 'Office 365 – Office Pro Plus Deployment Tool – An example'
date: '2015-01-19T12:23:07-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - Office365
    - Productivity
---

When you browse the Internet for use of the Office Deployment Tool for Click-to-Run for Office products you may find yourself lost in a myriad of websites referring to other websites and send you into several complete circles. There just too much out there if you just need to do a rollout for 5 or 10 PC’s. I thought I just make an example for the whole process.

Some background on my example. I have to do a rollout on 4 PC’s, last time I visited that location the Internet connection was terrible. And, I found out that users do not have a dedicated PC in the small Office. That gives me 2 good reasons to prepare the rollout using the Office Deployment Tool at home: no slow downloads on 4 PC’s and I can configure the shared computer activation.

On my Surface Pro3 I created a directory C:\\o365 and Shared it with Everyone (Read Permissions) as [\\\\jk-proi7\\o365](file:///\\jk-proi7\o365) .

![](http://www.kraak.com/wp-content/uploads/2015/01/011915_1622_Office365Of1.png)

In that directory I downloaded the Office Deployment Tool for Click-to-Run, you can find it here: <http://www.microsoft.com/en-us/download/details.aspx?id=36778> . Run “officedeploymenttool.exe” which creates only 2 files, so I’m left with 3 files in that directory:

![](http://www.kraak.com/wp-content/uploads/2015/01/011915_1622_Office365Of2.png)

Now I need to download the binaries of the Office Pro Plus in the language(s) I need and the versions (32 bits – 64 bits) I need. In my situation I only need the English 32 bits version so I edit, in Notepad, the “configuration.xml” file:

<span style="font-family:Courier New; font-size:8pt">&lt;Configuration&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Add SourcePath=”\\\\jk-proi7\\o365\\” OfficeClientEdition=”32″ &gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Product ID=”O365ProPlusRetail”&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Language ID=”en-us” /&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;/Product&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;/Add&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt">&lt;/Configuration&gt
-  
</span>

And I saved the file as “downloadus.xml” in that same directory, keeping everything together.

I’m ready to download now so I click Run and enter the following command:

<span style="font-family:Courier New
- font-size:8pt">\\\\jk-proi7\\o365\\setup.exe /download \\\\jk-proi7\\o365\\downloadus.xml</span>

I accept the UAC warning and a CMD Prompt Window opens with just a blinking cursor. That is bit annoying, no progress bar or what so ever. But in my directory I see files added and in Task Manager I can see my network is downloading at full speed. So stuff is happening, just wait until the CMD Prompt Window closes.

My o365 Directory now contains a folder “Office” which is just over 1 GB in size; the Office Pro Plus binaries!

For deploying Office Pro Plus I need to edit the “configuration.xml” once again and this time I save as “installus.xml”:

<span style="font-family:Courier New; font-size:8pt">&lt;Configuration&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Add SourcePath=”\\\\jk-proi7\\o365\\” OfficeClientEdition=”32″ &gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Product ID=”O365ProPlusRetail”&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Language ID=”en-us” /&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;/Product&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;/Add&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Display Level=”None” AcceptEULA=”TRUE” /&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt"> &lt;Property Name=”SharedComputerLicensing” Value=”1″ /&gt
-  
</span>

<span style="font-family:Courier New; font-size:8pt">&lt;/Configuration&gt
-  
</span>

Notice I used the Property Name to make sure that multiple users can run Office Apps on the machine after deployment. More on Shared Activation can be found here: <http://technet.microsoft.com/en-us/library/dn782860(v=office.15).aspx>

To install Office Pro Plus with these configuration settings I run the following command (with elevated privileges) on each machine:

 <span style="font-family:Courier New
- font-size:8pt">\\\\jk-proi7\\o365\\setup.exe /configure \\\\jk-proi7\\o365\\installus.xml</span>

Once again the nagging Command Prompt Window with no information. But look at Task Manager and folders being created, there is stuff happening on the PC.

Now all different users can logon to the PC and individually activate their Office Pro Plus.

A good starting point to read more on the whole process: <http://technet.microsoft.com/en-us/library/jj219422(v=office.15).aspx>
