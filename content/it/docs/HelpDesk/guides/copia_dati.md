---
weight: 630
title: "Copia Dati"
description: "Procedura per il trasferimento dati dal vecchio al nuovo laptop"
icon: "cloud_sync"
date: "2024-03-16T22:53:27+01:00"
lastmod: "2024-03-16T22:53:27+01:00"
draft: false
toc: true
---

### Procedura

{{% alert icon="💡" context="success" %}}
***Metodo:*** predisporre **sempre** i laptops e le cartrelle nel seguente ordine per non sbagliarsi mai
{{< table "table-striped table-responsive" >}}
| ⬅️ Vecchio Laptop  |   Nuovo Laptop ➡️   |
|--------------------|--------------------|
| ⬅️ Vecchia Cartella |    Nuova Cartella ➡️  |
{{< /table >}}
{{% /alert %}}

### Pre Copia Dati
1. Dal vecchio laptop » Login Utenza » Esportare preferiti e password
2. Login Admin su entrambi i laptop » collegarli tra loro via ethernet

### Dal Vecchio Laptop
1. Cambiare IPv4 Ethernnet in 192.168.1.1 
2. Disco C:\ » Proprietá » Condivisione » Condivisione Avanzata » **Condividi questa cartella** » **Permessi* » Spunta tutte le caselle

### Sul Nuovo Laptop
1. Cambiare IPv4 Ethernet in 192.168.1.2
2. Richiamare vecchio laptop da percorso di rete e predisporre le cartelle secondo metodo

### Copia Dati
1. Copiare le cartelle **Dati** e **Downloads**
2. Alla fine del trasferimento dati ripristinare impostazioni

### Dopo Copia Dati
1. Login Utenza » Windows Update
2. Importare Archivi Outlook
3. Importare Preferiti e Password
4. Check Java
5. Gpupdate » Riavvio » Ultimo check PaloAlto, Teams, Outlook ed LN


