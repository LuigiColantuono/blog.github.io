---
weight: 630
title: "In-Place"
description: "Procedure for Upgrading Dell Laptops to Win 10 LTSC Ent 22H2 M365"
icon: "system_update_alt"
date: "2024-03-16T22:53:27+01:00"
lastmod: "2024-03-16T22:53:27+01:00"
draft: false
toc: true
---

{{% alert icon="⚠️" context="warning" %}}
**Note:** Before you begin, connect your laptop to power and network cable!
{{% /alert %}}

### Pre-Upgrade - Enabling Tasks - Backup and Removing BeCrypt

1. Add CIXXXXXX to the shared file to have the upgrade uploaded to Software Center
2. User Login » WINVER `If you see 22H2 do not proceed` » Export Favorites and passwords
3. BeCrypt login as system » as Admin on Windows
5. Check disk space: At least 50GB required
6. Power Plan OFF
7. Check Cybereason Version 22.1.228.0 > if different update `\\srv-kitfgtfer01\Kit$\Application\Client\CR`
8. Back up: Data, Downloads, Temp, Bookmarks and PSW to: `\\srv-stobakprd01\hdbackup01$`
9. Check Becrypt Version: From the Windows tray » Right click on # » about BeCrypt
10. Copy same version from `\\srv-kitfgtfer01\kit$\Applications\Client\BeCrypt` into Temp.
11. Run BeCrypt the first time to start the decryption » Reboot when finished » Run BeCrypt one last time for permanent removal

{{% alert icon="⚠️" context="warning" %}}
Back up your user data and remove BeCrypt together to save time but don't reboot unless you're sure you've completed the backup!
{{% /alert %}}
   

### Upgrade - Win 10 LTSC Ent 22H2 M365


{{% alert icon="⚠️" context="warning" %}}
**Note:** If the task is confirmed but does not appear on Software Center » Control Panel » Configuration Manager » Actions and Execute tab:
1. Hardware inventory cycle
2. Computer policy evaluation and recovery cycle
3. Software inventory cycle
4. User policy recovery and evaluation cycle
{{% /alert %}}


5. From Software Center » Operating Systems » Start the available installation


{{% alert icon="💡" context="warning" %}}
**Note:** After the first restart, log in immediately to view the progress of the task; otherwise if you wait too long it will not be possible to view the progress task and the PC will appear to be doing nothing (but in reality it is working in the background); wait for the last reboot for the actual upgrade.
{{% /alert %}}


### After Upgrade

1. Check Windows Version » CMD » WINVER » Make sure it is 22H2.
2. From your PC » Check on AD User OU » Move PC to the corresponding OU in Windows10CB
3. Policy Update: gpupdate /force (Normal + Admin)
4. User Login » Windows Update + Update M365 (Account » Office Update » Update Now)
5. Reset Power Plan + Check Java & Excel Arabic » Bitlocker Installation (as admin)
6. gpupdate » Last reboot » Make sure GlobalProtect is connected, Teams and Outlook are connected, and everything is up to date.