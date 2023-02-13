---
title: 'Re-connecting a new Active Directory to an existing Office365 environment'
date: '2011-06-26T09:38:35-04:00'
author: jasper@kraak.com
tags:
    - Uncategorized
---

As a MCT I redeliver the Office365 Ignite Training. During the training each and every participant runs its own environment with its own domains and certificates. A couple of weeks ago we made in mistake in shutting down all the environments and deleting all student VMs. So there seemed to be no way to re-use the domains and the certificates.  
In Office365 you can only delete a domain when there are no longer objects in there. But you cannot delete synced objects except through the Directory Synchronization tool. When you deploy a new Active Directory with the same user accounts and run the Directory Synchronization tool you’ll get an error mail message to your tenant administrator mail address that the Object GUIDs do not match:

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/11.png "1")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/11.png)

So now it’s time to drill somewhat down in what the Directory Synchronization tool actually is. It runs on Identity Lifecycle Manager 2007 (ILM2007 SP1). ILM2007 is a very powerful tool for synchronizing all kind of flavor of directories. Be careful though, it’s power let you destruct both your on premises Active Directory and your Online Directory Services in a snap.  
You’ll find the client console for ILM2007 SP1 in:  
C:Program FilesMicrosoft Online Directory SyncSYNCBUSUIShellmiisclient.exe.  
In there, locate the following:

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/2.png "2")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/2.png)

And then,

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/3.png "3")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/3.png)

Click Edit and select “mail” in both the “Data source attribute” and the “Metaverse attribute” and click “Add Condition”.

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/4.png "4")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/4.png)

After that remove the source/Anchor condition (note: you’ll have to restore that after you’re done!)  
Click OK and the screen should look like:

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/5.png "5")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/5.png)

Click OK and click “Run” in the Actions Pane. Select the “Full Confirming Import” option and then OK.

[![](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/6.png "6")](http://kraakcom.azurewebsites.net/wp-content/uploads/2011/06/6.png)

This action will re-establish the connection between the on premises and the online accounts for each user object where there are identical mail addresses. (Note: perform the same procedure for the group and contact object types).  
There will be sufficient information available to see what actually happened.

When you’re done, force a Directory Sync with the Directory Synchronization Tool:  
C:Program FilesMicrosoft Online Directory Sync and run “DirSyncConfigShell”, in the Powershell window tyoe at the prompt: start-onlinecoexistencesync  
Wait a couple of minutes to see if you receive a mail message. If it doesn’t come, all is well. If it comes, check which accounts were not re-connected.

With thanks to MSFT, Michelle T. who gave me support through the Office365 Community Portal.
