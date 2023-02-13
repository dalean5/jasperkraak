---
title: 'Office365: Setting up SSO (ADFS) and DirSync'
date: '2011-03-12T20:13:56-04:00'
author: jasper@kraak.com
tags:
    - Uncategorized
---

**<span style="text-decoration:underline
-"> </span>**

**On a Domain Controller**

– Verify UPN Values in Active Directory:

 Import-Module Active Directory

 CD AD:

 Get-ADUser -Filter \* | FL UserPrincipalName

**On the ADFS Server**

– Install Microsoft Online Services Connector -&gt
- MSOnlineConnector-en.msi

– Install ADFS 2.0 -&gt
- ADFSSetUp.exe, Valid Public Certificate

– Install Microsoft Online Services Identity Federation Management Tool -&gt
- FederationConfig.msi

– Add a Federated Domain -&gt; Microsoft Online Services Identity Federation Management Tool -&gt
- PowerShell opens

(Note: the DomainName mentioned here is already taken…..by me :-))

 $cred = Get-Credential

 Set-MSOLContextCredential -MSOLAdminCredentials $cred

 Add-MSOLFederatedDomain -DomainName 365onnebula.net

WARNING: Please verify 365onnebula.net ownership by adding a DNS ms12345678.365onnebula.net CNAME record targeting ps.microsoftonline.com

– Add CNAME Record in Public DNS, wait 5-15 minutes, rerun:

 Add-MSOLFederatedDomain -DomainName 365onnebula.net

 Get-MSOLFederationProperty -DomainName 365onnebula.net

– The output of both your local ADFS Server and MicrosoftOnline should be exactly the same!!

**On the Directory Synchronization Server**

This must be a 32-bits Server OS (x86), member of the domain but not a Domain Controller.

To enbale Directory Synchronization go to:

– https://portal.microsoftonline.com -&gt; Admin -&gt; Domains -&gt
- Activate Active Directory Synchronization

– Install dirsync.exe (x-32 only, not on a Domain Controller), and follow the procedure. By default synchronization occurs every three hours. To force synchronization:

– Run DirSyncConfigShell.pcs1 -&gt
- PowerShell opens

 Start-OnlineCoexistenceSync
