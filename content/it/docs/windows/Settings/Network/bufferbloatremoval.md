---
weight: 401
title: Ridurre"Buffer Bloat"
description: "Impostazioni per migliorare la connessione e ridurre la latenza!" 
icon: network_check
date: 2022-11-22T12:36:15+00:00
lastmod: 2022-11-22T12:36:15+00:00
draft: false
images: []
---

### Panoramica Scheda di Rete
> ###### Per accedere alle impostazioni della tua scheda di rete vai a `Start` ― `Pannello di Controllo` ― `Rete e Internet` ― `Centro connessioni di rete` ― `Modifica impostazioni scheda` ― Tasto destro su Ethernet e seleziona Proprietá 

![alt text](https://i.imgur.com/SRexdT4.png)

Di default Windows lascia attivi molti elementi che vanno a stressare la connessione, si consiglia di lasciare attivo solo il Protocollo IPv4 e il QoS.

**Disattivare Risparmio Energetico**

![alt text](https://i.imgur.com/vwAGSDk.png)

### Ethernet Controller Properties Advanced 
> ###### Da `Proprietá - Ethernet`, clicca su `Configura` e seleziona la tab `Avanzate` per accedere alle impostazioni.

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

### Comandi Utili
Per eseguire i comandi puoi usare Terminal, CMD oppure Powershell.

##### Display TCP Global Parameters
Essere sicuri che `Auto-Tuning Level` sia impostato su `Normal`
```sh
netsh interface tcp show global
```

> ###### Per impostare **Auto-Tuning Level** sono disponibili 5 livelli, usa il seguente comando per impostarne uno.
> ###### Di Default dovrebbe essere impostato su Normal.
> ###### Disattivarlo potrebbe migliorare la latenza ma potrebbe anche ridurre/limitare la velocitá di upload e download!

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


