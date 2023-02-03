---
title: 'Break Glass Account using FEITIAN FIDO2 Key'
date: '2023-01-03T09:24:20-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - Office365
---

I was invited by Della (FEITIAN Technologies) to review one of their FIDO2 products. Out of their range of products I choose the K50: USB A-Type with Fingerprint.

There is one particular use case for using a FIDO2 Fingerprint Key I’d like to examine. The Break Glass (Global Admin) Account. By now, in 2023, we all agree on Multi Factor Authentication for ALL Users and we’re moving fast forward to Passwordless Authentication. In the Trainings I deliver and in conversations with my Customers we always discuss the “Break Glass Account” for emergencies. Shouldn’t we have a non-MFA-enabled Account for that? Write a very complex password on a piece of paper and put it in a safe?

No more. For daily use of both normal users and privileged users the Authenticator App works just fine. I’m not so much in favor of adding another device. For privileged accounts we should add Conditional Access policies like Device Compliance (Windows 11 Enterprise with all Security Features enabled), location and such. And Privileged Identity Management to harden access security (Principle of Least Privilege and Just-Intime Access).

And then we run into an emergency situation….. the hardened workstations become inaccessible or cellular Wi-Fi Services become unavailable (no push notification to Authenticator app) or whatever trouble.

In situations like that, having some FIDO2 Keys on some Break Glass Accounts can be a very good solution. Restrict these accounts to authenticating ONLY with a Security Key. Have 3-5 Accounts and a couple of these Keys (you can add up to 128 accounts on 1 Key). Enroll all 3-5 accounts on all Keys and keep the Keys in separate places for redundancy. Don’t forget to put PIM on these Accounts!

Et voila! We have a very decent solution in place, compliant with the MFA Policy for ALL users and also Passwordless.

Break the Glass safely!