---
weight: 401
title: "Buffer Bloat Removal"
description: "Settings to minimize latency and improve connection!"
icon: network_check
date: 2022-11-22T12:36:15+00:00
lastmod: 2022-11-22T12:36:15+00:00
draft: false
images: []
---

### Network Adapter Overview
> ###### To access your Network Adapter Settings go to `Start` ― `Control Panel` ― `Network and Sharing Center` ― `Change Adapter Settings` ― `Ethernet Properties` ― `Networking`

![alt text](https://i.imgur.com/SRexdT4.png)

By default Windows leaves many items active that stress the connection, you can deselect everything and leave only IPv4, and if necessary also QoS.
**Disable Power Saving**

![alt text](https://i.imgur.com/vwAGSDk.png)

### Ethernet Controller Properties Advanced 
> ###### From `Ethernet Properties`, click the `Configure` button and then select the `Advanced` tab to access the advanced settings.

{{< table "table-striped-columns table-responsive " >}}
| Property | Value |
|---------|--------|
| `ARP Offload` |  Disabled | 
| `DMA Coalescing` |  Disabled |  
| `Enable PME` | Disabled | 
| `Energy Efficient Ethernet` | Off |  
| `Flow Control` | Disabled | 
| `Interrupt Moderation` | Disabled | 
| `Interrupt Moderation Rate:` | Off | 
| `IPv4 Checksum Offload` | Disabled | 
| `Jumbo Packet` | 9000 | 
| `Large Send Offload V2(IPv4)` | Disabled | 
| `Large Send Offload V2(IPv6)` | Disabled | 
| `Log Link State Event` | Disabled | 
| `NS Offload` | Disabled | 
| `Packet Priority & VLAN` | Packet Priority & VLAN Disabled | 
| `Receive Buffer` | 1024 | 
| `Speed & Duplex` | 1~10 Gbps Full Duplex | 
| `TCP Checksum Offload (IPv4)` | Disabled | 
| `TCP Checksum Offload (IPv6)` | Disabled | 
| `Transmit Buffer` | 2048 | 
| `UDP Checksum Offload (IPv4)` | Disabled | 
| `UDP Checksum Offload (IPv6)` | Disabled | 
| `Wait for Link` | Off | 
| `Wake from S0ix on Magic Packet` | Disabled | 
| `Wake on Link Settings` | Disabled | 
| `Wake on Magic Packet` | Disabled |
| `Wake on Pattern Match` | Disabled |
{{< /table >}}

### Useful commands
To run commands you can use Terminal, CMD or Powershell.

##### Display TCP Global Parameters
Make sure `Auto-Tuning Level` is set to `Normal`
```sh
netsh interface tcp show global
```

> ###### To manage the **Auto-Tuning Level** there are 5 levels available, use the following command to set one.
> ###### In most cases it is set to normal by default.
> ###### Disabling it can improve latency but can reduce or limit download and upload speed!

{{< table "table-striped-columns table-responsive " >}}
| Level | Value |
|---------|--------|
| `Normal` | 0x8 (scale factor of 8) | 	
| `Disabled` | No scale factor available | 	
| `Restricted` | 0x4 (scale factor of 4) | 	
| `Highly Restricted` | 0x2 (scale factor of 2) |	
| `Experimental` | 0xE (scale factor of 14) |
{{< /table >}}

```sh
netsh interface tcp set global autotuninglevel=disabled
```


