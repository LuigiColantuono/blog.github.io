---
weight: 610
author: "Luigi Colantuono"
title: "Oracle & LnTools"
description: "Oracle Installation Guide and LnTools Configuration"
icon: "database"
date: "2024-03-17T08:32:20+01:00"
lastmod: "2024-03-17T08:32:20+01:00"
draft: false
toc: true
tag: ezpz
---

## Requirements

The installation files are available in this path

```treeview
StarterKit/
└── Software/
    └── Oracle_LnTools/
        ├── Oracle_11.2.0_x64/
        ├── Oracle_Deinstall/
        └── LnTools_v3/
```

## Installation

{{% alert icon="⚠️" context="warning" %}}
Before installing Oracle I recommend creating the directories manually to avoid any duplicate folders.

**Oracle Base**
`C:\Program Files\Oracle`

**Software Location**
`C:\Oracle\11.2.0`
{{% /alert %}}

1. Run Oracle_11.2.0_x64.exe > Choose Custom > Next > Next
2. Oracle Base Path: `C:\Program Files\Oracle`
3. Software Path: `C:\Oracle\11.2.0`
4. Next > Select Components:
5. SQL Plus
6. Oracle Call Interface (OCI)
7. Oracle Net
8. Oracle ODBC Driver
9. Oracle Object for OLE DB
10. Oracle Data Provider for .NET

## Deinstall
```shell
cd C:\StarterKit\Software\Oracle_LnTools\Oracle_Deinstall
Deinstall -home C:\Oracle\11.2.0
```

## LnTools

1. Copy .dll and .ocx files in `C:\Windows\System32` and `C:\Windows\SysWOW64`
2. Active .dll and .ocx » **regsvr32** `name.dll` and `name.ocx`
3. Copy **.ora** files in `C:\Oracle\11.2.0\Network\Admin` 
4. Copy **LnTools_v3.xla** in `C:\Users\%UserProfile%\AppData\Roaming\Microsoft\Addins`
5. Open Excel » File » Options » Add-ins » Go... » Browse...
6. Select **LnTools_v3.xla** and check it ✔

### Test if it actually works!

1. In Excel, type **879820** in a cell
2. in the **next cell** type **=giacenza(**
3. **Select cell 879820** and close brackets **)**
4. Press Enter and **if it returns 21 it works!**
