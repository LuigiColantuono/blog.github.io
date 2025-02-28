---
weight: 610
date: "2024-03-16T23:03:22+01:00"
draft: false
author: "Colantuono Luigi"
title: "Basic Setup"
icon: "laptop_chromebook"
toc: true
language: "English"
description: "Dell Laptops - Standard Configuration!"
publishdate: "2023-05-03T22:37:22+01:00"
tags: ["Beginners"]
---


##### Standard Setup for Windows 10 LTSC 22H2 M365 OS Installation
-------------------------------------------------------------------------------

### Prerequisites
> **Make sure to connect the power cord and network cable to the laptop
Press F2 repeatedly to enter bios**

### Bios configuration

{{< table "table-striped-columns table-responsive " >}}
| Setting | Param |
|---------|--------|-----|
| `Boot Configuration` | Uncheck IPv6 |
| `Storage` | Select AHCI |
| `Integrated Devices` | Select 24H |
| `Password` | bfkm4 |
{{< /table >}}

. Apply Changes » Exit » Spam F12 to access BOOT

### OS installation
1. Select: IPV4
2. Enter: bfkm4
3. Enter: FerrariGT
4. Select: 22H2 M365
5. Enter: CIXXXXXX

### Configuration from Admin user
1. Log in with your admin account » Launch Windows Update
2. Edit Power Plan: All Never » Power Option » System Settings » Shout Down (2 above), Do Nothing for the rest
3. Settings » Time & Language » Language: Italian » No, sign me out later » Administrative language settings » Copy Settings » Check New User Account
4. From the personal Temp, copy StarterKit to the user's Temp » Install Chrome and java


### OU configuration
1. From your PC, run Active Directory as Administrator
2. Action » Find » Select Users, Contacts, and Groups » Enter Username » Find Now » Double click on the user » Leave window open
3. Select Computers » Enter CIXXXXXX » Double click on the Computer » General Tab » Fill in the Description field respecting the following formatting:
    ```[Surname, Name - Cost Center - Department - PPC] - (info available from the user's general tab)```
4. In the User Properties Tab » Object Tab » Check User OU » Right-click on Computer » Move » Move Computer to the corresponding OU in Windows10CB\Laptop


### NTRights
1. On the user's PC » Admin Login » Copy path C:\Temp\StarterKit\Ntrights
2. Run ntrights.bat as administrator » Paste previously copied path » Enter the following information:
3. ➊ Enter Username (Available on AD » User Properties Tab » Account Tab)
4. ➋ Local Administrator Password: Admincixxxxxx (computer name)
5. ➌ Cost Center - Asset - Surname, Name - Department (Available on AD » User properties tab » General Tab)
  
### User Configuration
1. Log in with your user credentials » Add printer connection from \\srv-prtappfgt01
2. Search BECS » Select the only line present » Tools » Options » Public.
3. Configure Java » Edit Site List » Add the **Java exception link** present in the StarterKit to the exceptions.
4. Settings » Personalization » Themes » Desktop Icon Settings » Check **User Files** » Apply » Ok.
5. Desktop » Open User Folder » Delete the 6 double folders » Create **Data** Folder » Inside Data create **Outlook** folder

### Outlook configuration
1. Control Panel » View by Small Icons » Mail (Microsoft Outlook) » Add » Username (Account) » Ok » Next.
2. Uncheck Outlook Mobile » Tick 𝗖𝗮𝗺𝗯𝗶𝗮 𝗜𝗺𝗽𝗼𝘀𝘁𝗮𝘇𝗶𝗼𝗻𝗶 𝗔𝗰𝗰𝗼𝘂𝗻𝘁 » Next » Mail to keep offline: MAX » Other Settings.
3. Advanced Settings » Uncheck download shared folders » Outlook Data File Settings » Save the file in the Outlook Folder created previously leaving only the username.