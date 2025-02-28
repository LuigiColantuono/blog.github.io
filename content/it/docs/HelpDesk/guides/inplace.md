---
weight: 620
title: "InPlace"
description: "Procedura per l`upgrade dei laptop Dell 55XX alla versione 22H2 M365"
icon: "system_update_alt"
date: "2024-03-16T22:53:27+01:00"
lastmod: "2024-03-16T22:53:27+01:00"
draft: false
toc: true
---


{{% alert icon="⚠️" context="warning" %}}
**Note:** Prima di iniziare, collegare il laptop all'alimentazione e al cavo di rete!
{{% /alert %}}


### PreUpgrade - Abilitazione Task  - backup e Rimozione BeCrypt 

1. Comunicare CIXXXX per inserimento Upgrade su SoftwareCenter  
2. Login Utenza » Esportare Preferiti e password
3. BeCrypt login come system » come admin su Windows
4. WINVER `Se visualizzi 22H2 non procedere`.
5. Check spazio su disco: Richiesti almeno 50GB.
6. Risparmio Energetico OFF.
7. Check Versione Cybereason 22.1.228.0 > se diversa aggiornare \\srv-kitfgtfer01\Kit$\Application\Client\CR 
8. Effettuare il backup di: Dati, Download, Temp, Preferiti e PSW in: `\\srv-stobakprd01\hdbackup01$`
9. Check Versione Becrypt: Dalla tray di Windows » Tasto dx su # » about BeCrypt.
10. Copiare stessa versione da `\\srv-kitfgtfer01\kit$\Applications\Client\BeCrypt` nella Temp.
11. Eseguire BeCrypt la prima volta per avviare la decriptazione » Al termine riavvio » Eseguire BeCrypt un ultima volta per la rimozione definitiva

{{% alert icon="⚠️" context="warning" %}}
Effettuare il backup dei dati e la decriptazione insieme per risparmiare tempo ma non eseguire il reboot se non si é certi di avert completato il backup!
{{% /alert %}}
   

### Upgrade - Windows 10 22H2 M365  


{{% alert icon="⚠️" context="warning" %}}
**Note:**  Se l'inserimento éconfermato ma non poppa su Software Center » Pannello di controllo » Configuration Manager » Tab Azioni ed Eseguire: 
1. Ciclo di inventario hardware             
2. Ciclo di recupero e valutazione criteri computer
3. Ciclo di inventario software              
4. Ciclo di recupero e valutazione criteri utente
{{% /alert %}}


5. Da Software Center » Sistemi Operativi » Avviare l’installazione disponibile 


{{% alert icon="💡" context="warning" %}}
**Note:**  Dopo il primo riavvio loggarsi immediatamente per visualizzare l'avanzamento della task; altrimenti il pc sembrerà non fare nulla (ma in realtá sta lavorando in background); attendere l'ultimo riavvio per l'upgrade definitivo.
{{% /alert %}}


### Dopo Upgrade 

1. Check Versione Windows » CMD » WINVER » Assicurarsi che sia 22H2.
2. Dal proprio PC » Verificare su AD OU Utente » Spostare PC nella OU corrispettiva in Windows10CB 
3. Policy Update:  gpupdate  /force (Normale + Admin)
4. Update M365 (Account » Office Update » Update Now) + Windows Update
5. Login da Utenza » Installazione Bitlocker (come admin) 
6. Reimpostare Risparmio Energetico + Check Java & Excel Arabo 
7. gpupdate » Ultimo riavvio » Accertarsi che Teams e Outlook si connettano via PaloAlto e che tutto sia aggiornato.
