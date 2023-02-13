---
title: 'Redefine Backup for Online Services'
date: '2013-01-22T20:07:53-04:00'
author: jasper@kraak.com
tags:
    - 'Cloud Computing'
    - Office365
    - backup
---

I see a lot of questions in all sort of forums on backups. And I think it might be worth an effort to redefine what we mean and want to accomplish wit backups.

In the old days my definition of backup was that it’s only the preparation for a restore. Some file or system gets lost or corrupted, you look in your backups for a moment in time that the file or system was still working and you restore the file or system back to that point in time. That approach might lead to data loss of recent modifications to the file or system. When was the backup created and what happened to the file or system since that moment in time. We call that Recovery Point Objective (RPO), the data loss window. Next to RPO we haven RTO, Recovery Time Objective; how much time does it take to have systems or files available for use after a disruption. And last but not least, how far back in time do we want to go for recovery of files or systems

A lot of people tend to confuse a backup with an Archive. The purpose of an archive however is not to restore things to a certain point back in time, it’s about the ability to look up things from the past. So let’s have those two clearly distinct from each other: backup is no archive!

Looking at Online Services, like Exchange Online, are backups available in that environment? Well, they are not available to users. Microsoft only uses backup technologies for continuity of service and data integrity. That means there is no way of getting back a deleted mail item once all retention periods have been expired. Not one way. The same goes for SharePoint Online. Exchange also has a feature called Litigation Hold, from a mailbox placed under that policy, items can never be deleted. Not accidentally and not on purpose. Running Exchange on premises with DAGs is also about continuity, when setup across multiple datacenters, there’s also no need for backups.

Is that bad? I don’t think so. If Microsoft guarantees continuity of service and data integrity then it’s up to users to deal with that data. The retention policies allow for enough time to recover accidentally deleted items and for the rest I don’t see any reason at all for having backups, considering that a backup is NOT an archive.

I am not suggesting we stop making backups but we can be more aware of the why, when, where and how. Could save a bit money <span style="font-family:Wingdings">J</span>.
