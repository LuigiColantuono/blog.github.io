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

##### Setup Standard per Installazione OS Windows 10 LTSC 22H2 M365
------------------------------------------------------------------------------

### Prerequisiti
> **Assicurarsi di collegare al laptop il cavo di alimentazione e il cavo di rete
Premere ripetutamente F2 per accedere al bios**

### Configurazione Bios
1. Boot Configuration: Deselezionare IPV6 
2. Storage: Seleziona AHCI
3. Integrated Devices: Seleziona 24H
4. Password: bfkm4
5. Apply Changes » Exit » Spam F12 per accedere al BOOT

### Installazione OS
1. Seleziona: IPV4 
2. Inserire: bfkm4
3. Inserire: FerrariGT 
4. Seleziona: 22H2 M365
5. Inserire: CIXXXXXX

### Configurazione da utenza Admin
1. Accedere con la propria utenza admin » Lanciare Windows Update
2. Edit Power Plan: Tutto Never » Power Option » System Settings » Shout Down (2 sopra), Do Nothing per il resto
3. Settings » Time & Language » Language: Italiano » No, sign me out later » Administrative language settings » Copy Settings » Spuntare New User Account
4. Dalla Temp personale, copiare StarterKit nella Temp dell'utente » Installare Chrome e java


### Configurazione OU
1. Dal proprio PC eseguire Active Directory come Amministratore
2. Azione » Find » Seleziona Users, Contacs, and Groups » Inserire Nome Utente »  Find Now » Doppio click sull'utente » Lasciare finiestra aperta
3. Seleziona Computers » Inserisci CIXXXXXX » Doppio click sul Computer » Tab Generale » Compilare il campo Descrizione rispettando la seguente formattazione:
   ```[Cognome, Nome - Centro di Costo - Reparto - PPC] - (info reperibili dalla tab generale dell'utente)```
4. Nella Scheda proprietà utente » Tab Oggetto » Check OU utente » Tasto DX sul Computer » Move » Spostare Computer Nella corrispettiva OU in Windows10CB\Laptop


### NTRights
1. Sul PC dell'utente » Login Admin » Copiare percorso C:\Temp\StarterKit\Ntrights
2. Eseguite ntrights.bat come amministratore » Incollare percorso copiato in precedenza » Inserire le seguenti info:
3. ➊ Inserire Nome Utente (Reperibile su AD » Scheda proprietà utente » Tab Account)
4. ➋ Password Amministratore Locale: Admincixxxxxx (nome del computer)
5. ➌ Centro di Costo - Asset - Cognome, Nome - Reparto (Reperibile su AD » Scheda proprietà utente » Tab Generale)
  
### Configurazione Utente 
1. Accedere con le credenziali dell'utente » Aggiungere collegamento stampante da \\srv-prtappfgt01
2. Cerca BECS » Selezionare unica riga presente » Tools » Options » Public.
3. Configure Java » Modifica Lista Siti » Aggiungere tra le eccezioni il **link eccezione Java** presente nello StarterKit.
4. Impostazioni » Personalizzazione » Temi » Impostazioni Icone del Desktop » Spuntare **File Utente** » Applica » Ok.
5. Desktop » Aprire Cartella Utente » Eliminare le 6 cartelle doppie » Creare Cartella **Dati** » Dentro Dati creare cartella **Outlook**

### Configurazione Outlook
1. Pannello di Controllo » Visualizza per Icone Piccole » Mail (Microsoft Outlook) » Aggiungi » Nome Utente (Account) » Ok » Avanti.
2. Deselezionare Outlook Mobile » Spuntare **Cambia Impostazioni Account** » Avanti » Posta da mantenere offline: MAX » Altre Impostazioni.
3. Impostazioni Avanzate » Deselezionare scarica cartelle condivise » Impostazioni File Dati di Outlook » Salvare il file nella Cartella Outlook creata in precedenza lasciando solo il nome utente.
