---
title: 'Update Certificates in AD FS for Office365'
date: '2012-07-07T21:40:25-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - Office365
---

As Office365 was launched just over a year ago, there will be organizations that will run into an issue with their AD FS (SSO) implementation, the result of which is that NO FEDERATED USER is able to Sign In to any of the Office 365 Services!!!!

Set it and forget it works for just 1 year if you implemented AD FS the fast and easy way. A couple of things might have happened in those 12 months:

– Token Signing Certificate is expired

– MSOL Services Module for Windows Powerhell has not been updated

– Sign In URL Certificate is expired

In this blog post I’ll do a walkthrough of the update process of the first two from this list. The web service (Sign In URL) probably involves a public certificate and has to be updated through IIS Management console after renewing your public web certificate.

Of course it is best to do this BEFORE the expiration dates!!!!

The starting point for renewing the Token Signing Certificate is taking a look a the current settings in both AD FS Management Console and MSOL Powershell:

Open MSOL Services Module for Windows Powershell and enter the following commands:

***$cred = Get-Credential*** (enter your Online Admin credentials)

***Connect-MsolService -Credential $cred***

***Set-MsolADFSContext –Computer &lt;your adfs servername&gt
-***

***Get-MSOLFederationProperty –DomainNam**e &lt;your domainname***&gt
-

The output looks something like this:![pic1](http://www.kraak.com/wp-content/uploads/2012/07/pic1-150x150.png)

Have a close look at the Token Signing Certificate “not after” date and the thumbprint, which are both equal on Source: “your AD FS Server” and on Source “Microsoft Office365”.

The second step is to verify the current settings in the AD FS Management console:[![pic2](http://www.kraak.com/wp-content/uploads/2012/07/pic2-150x150.png)](http://www.kraak.com/wp-content/uploads/2012/07/pic2.png)

In this console you click “Add Token-Signing Certificate:[![pic3](http://www.kraak.com/wp-content/uploads/2012/07/pic3-150x150.png)](http://www.kraak.com/wp-content/uploads/2012/07/pic3.png)

Probably you’ll end up was this warning and this Wizard will not continue, fortunately the warning gives us exact information on how to add a new certificate to AD FS:[![pic4](http://www.kraak.com/wp-content/uploads/2012/07/pic4-150x140.png)](http://www.kraak.com/wp-content/uploads/2012/07/pic4.png)

Open Powershell as Administrator and run:

***Add-PSSnapin Microsoft.Adfs.Powershell***

***Update-ADFSCertificate -CertificateType: Token-Signing -Urgent:$true***

You can check the new certificate by looking at the date in the AD FS Management Console:![pic6](http://www.kraak.com/wp-content/uploads/2012/07/pic6-150x127.png)

Now we have to update the Microsoft Federation Gateway with this newly created certificate on our AD FS Server because there is a difference between the settings on the two.[![pic7](http://www.kraak.com/wp-content/uploads/2012/07/pic7-150x150.png)](http://www.kraak.com/wp-content/uploads/2012/07/pic7.png)

The command for doing that is:

***Update-MSOLFederatedDomain –DomainName &lt;your domainname&gt
-***

Check the result by entering the following command:

***Get-MSOLFederationProperty –DomainName &lt;your domainname&gt
-***[![pic8](http://www.kraak.com/wp-content/uploads/2012/07/pic8-150x150.png)](http://www.kraak.com/wp-content/uploads/2012/07/pic8.png)

If you did not use the self-signed certificate in AD FS but assigned certificates through your local PKI please see the following website: <http://support.microsoft.com/kb/2383983> .

To avoid any issues of this kind you can use the **Microsoft Office 365 Federation Metadata Update Automation Installation Tool which you can download from:**

<http://gallery.technet.microsoft.com/scriptcenter/Office-365-Federation-27410bdc>

Finally, it might be a good idea to check if you are using the latest version of the MSOL Service Module for Windows Powershell. For as far as I know this tool is not automatically updated by Windows Update.

Good Luck!
