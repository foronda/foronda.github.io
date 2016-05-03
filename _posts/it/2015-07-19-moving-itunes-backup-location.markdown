---
layout: post
title: "How to Move iTunes Backup Location"
headline: Free up valuable SSD space on your C drive.
description: Change iTunes backup location using Windows mklink junction command.
categories: IT
tags: 
  - how-to
  - itunes
published: true
---

###Problem: 
Operating system (C:) drive running out of space due to iTunes backup.This is very useful if your OS runs on SSD (which is common today) to save valuable space.

###Solution: 
Change the backup location of iTunes using Windows mklink junction command.

###Procedure:
1. Rename the backup folder under %AppData%\Apple Computer\MobileSync\Backup to Backup-old
2. Create the new folder location i.e (D: iTunes Backup)
3. Run the junction command.

```
mklink /j "%appdata%\Apple Computer\MobileSync\Backup" "D:\iTunes Backup
```
----------

###References:

1. http://www.howtogeek.com/164275/how-to-change-the-backup-location-of-itunes-or-any-windows-app/
2. http://social.technet.microsoft.com/Forums/en-US/8700d04f-45b6-45db-bab5-48bd86a69e18/mklink-error-the-syntax-of-the-command-is-incorrect?forum=w8itprogeneral
