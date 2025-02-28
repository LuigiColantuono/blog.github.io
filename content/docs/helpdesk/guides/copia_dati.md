---
weight: 620
title: "Data Transfer"
description: "Procedure for transferring data from old to new laptop"
icon: "cloud_sync"
date: "2024-03-16T22:53:27+01:00"
lastmod: "2024-03-16T22:53:27+01:00"
draft: false
toc: true
---

### Method

{{% alert icon="💡" context="success" %}}
***Always*** arrange the laptops and folders in the following order to never make mistakes!
{{< table "table-responsive" >}}
| 🢠 To the left   |   To the right 🢡 | 
|-----------------|:--------------:|
|  Old Laptop   |   New Laptop  | 
| Old Folder   |   New Folder  |
{{< /table >}}
{{% /alert %}}


### Pre - Data Transfer
1. User Login » **Export Bookmarks and Passwords**
2. Admin Login on both laptops » connect them to each other via ethernet

### From the Old Laptop
1. Change Ethernet IPv4 to **192.168.1.1**
2. Drive **C:**\ » Properties » Sharing » **Advanced Sharing** » **Share this folder** » **Permissions* » Check all boxes

### On the New Laptop
1. Change Ethernet IPv4 to **192.168.1.2**
2. Recall old laptop from network path and arrange folders according to the method

### Data Transfer
1. **Copy** the **Data** and **Downloads** folders
2. At the end of the data transfer restore settings

### After Data Transfer
1. User Login » Windows Update
2. Import Outlook Archives
3. Import Bookmarks and Passwords
4. Check Java
5. Gpupdate » Restart » Last check PaloAlto, Teams, Outlook and LN

