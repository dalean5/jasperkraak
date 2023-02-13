---
title: 'Accounts, Identities and mail addresses'
date: '2015-02-11T09:47:53-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - MCT
    - 'Microsoft Azure'
    - Office365
    - Productivity
---

Users want to access applications and data that run anywhere, and, they want to run them from anywhere. There is only a very thin line left distinguishing business apps from non-business apps and they all need to be accessible anytime, anyplace, anywhere. That calls for Identity Management which can be very confusing for users. So here is a little explanation on the why, the what and the how.

In the old days we used to logon to our computer using this format:

- Domain\\user
- Computer\\user

Or maybe even without the domain\\ or computer\\:

- User (domain user)
- User (local computer user)

As long as the applications and their data sat on that local computer or in that local Active Directory domain, a logon like this worked perfectly. (Really? No. It uses NetBIOS and that protocol is soooo 1987, but that discussion is out of scope for this article)

The logon identity for a user must now be valid outside of the local computer and the local Active Directory as well. It must identify the user as a unique identity across multiple platforms, preferably: local computer, Active Directory, cloud applications like Office365 and personal applications like Facebook, Gmail, Twitter and the rest of it all.

The format to logon is called User Principal Name and a UPN looks like an email address and that can be very confusing for some users, for example:

- <firstname.lastname@domain.com>

NOTE: this is NOT necessarily a mail address! A mail address for this user could be, for example:

- <firstinitiallastname@companydomain.com>

If your computer is running Windows 8 (or above) you can logon using a Microsoft Account (a.k.a. LiveID or Hotmail.com or outlook.com account). The format of such an account is always the UPN format and it may or may not correspond to your private email account.

If you use multiple devices like PC, laptop, tablet, Windows Phone, the Microsoft Account synchronizes a lot of settings between your devices (like recent documents, desktop wallpaper, etc.) so that the user experiences a unified work environment, on whatever device.

Next to having a Microsoft Account (private, individual) you can have an Active Directory account to access corporate resources in your corporate network, maybe even remotely. Active Directory can (and should) have UPN as logon format instead of the NetBIOS domain\\user.

When using Microsoft Online services like Office365, Microsoft Intune or Microsoft Azure you may have a so called Organizational Account, always in the format of a UPN. It can be synchronized from your Active Directory account, even with synchronization of your password. But beware, unless a thing called Federated Identities is enabled by your administrators, it still is 2 separate identities; you logon to separate authentication providers, your local Active Directory and a Cloud Authentication provider like Azure Active Directory.

So until now, this is all on accounts, the mechanism with which you authenticate yourself. Now we get to email addresses.

An email address always comes in the format of UPN (actually UPN’s were there first and email addresses were derived from the UPN). As noted above, the account does not necessarily have to match an email address. It can but it is not a requirement.

And that is exactly what can make it very confusing for users if they do not distinguish the difference between accounts (UPN, identity) and email addresses. THEY ARE TWO DIFFERENT THINGS! A user can sign with one UPN and have access through that to multiple mail addresses (aliases) even in different domains.

Some organizations and users try to match the account UPN to the email address, making it simple for users: who you are (account UPN) is your mail address. It gets confusing when you have multiple accounts AND multiple email addresses. In order to get it straightened out for yourselves you can create a little table like this and fill out the appropriate UPN’s:

<div>| Access to | Microsoft Account | Active Directory Account | Organizational Account |
|---|---|---|---|
| Devices |  |  |  |
| Active Directory |  |  |  |
| Online Services |  |  |  |
| Office ProPlus |  |  |  |
| Work email |  |  |  |
| Private email |  |  |  |

</div>Happy logging on!
