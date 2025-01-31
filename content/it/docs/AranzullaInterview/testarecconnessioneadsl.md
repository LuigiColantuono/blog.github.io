---
weight: 602
title: "Come Testare una Connessione ADSL o Fibra"
description: "Guida Completa su Come Testare una Connessione ADSL o Fibra"
icon: article
date: 2022-11-22T12:36:15+00:00
lastmod: 2022-11-22T12:36:15+00:00
draft: false
images: []
---

La velocità e la qualità di una connessione internet sono fondamentali per qualsiasi tipo di utilizzo: dallo streaming di contenuti, al gaming, fino al lavoro da remoto.<br>
Testare una connessione ADSL o Fibra è importante per capire se stai ricevendo ciò per cui stai pagando, se ci sono problemi di prestazioni o se il tuo provider sta effettivamente offrendo la velocità promessa.<br>
In questa guida dettagliata vedremo tutti i passaggi necessari per testare correttamente una connessione ADSL o Fibra, dall’utilizzo di strumenti online a test più avanzati, per identificare eventuali problemi e risolverli.

---

### 1. Introduzione alla Connessione ADSL e Fibra

Le connessioni ADSL e Fibra ottica sono due delle tecnologie più comuni per la connessione a Internet nelle case e negli uffici. Ecco una breve panoramica delle differenze:

- **ADSL (Asymmetric Digital Subscriber Line)**: È una connessione via cavo che utilizza la rete telefonica tradizionale (in rame) per trasmettere i dati. Offre una velocità di download più alta rispetto al upload, ed è generalmente più lenta rispetto alla fibra.
  
- **Fibra Ottica**: Questa tecnologia utilizza fibre ottiche per trasmettere dati alla velocità della luce, offrendo connessioni molto più veloci rispetto all'ADSL, sia per il download che per l'upload. La fibra può essere di due tipi: Fibra fino a casa (FTTH) e Fibra fino all’armadio (FTTC).

Testare una connessione ADSL o fibra è essenziale per assicurarsi che il servizio funzioni correttamente e che la velocità raggiunga i livelli promessi dal contratto. In questa guida, esploreremo come eseguire i test per entrambe le tecnologie.

### 2. Strumenti Utilizzati per Testare la Connessione

Per testare la tua connessione internet, ci sono diversi strumenti che puoi utilizzare. Alcuni sono online, mentre altri richiedono software da installare. Di seguito sono elencati i principali strumenti di test:

- **[Speedtest.net](https://www.speedtest.net/)**: Uno degli strumenti di test di velocità più utilizzati a livello globale. Permette di testare la velocità di download, upload e ping.
  
- **[Fast.com](https://fast.com/)**: Un test di velocità sviluppato da Netflix, particolarmente utile per testare le prestazioni di streaming.

- **[Waveform - Bufferbloat and Internet Speed Test](https://www.waveform.com/tools/bufferbloat)**: Speed test utile per gaming e streaming per valutare ping, jitter e carichi sulla connessione e ottenere un grado della tua connessione.

- **[Ne.Me.Sys](https://misurainternet.it/login/?next=/download/nemesys/)** unico strumento che abbia un qualche valore legale, software distribuito da AGCOM (l’Autorità per le Garanzie nelle Comunicazioni) che si installa sul computer e monitora la velocità della connessione nell’arco delle 24 ore.

- **Traceroute**: Uno strumento che permette di tracciare il percorso dei pacchetti attraverso la rete, identificando eventuali colli di bottiglia o problemi lungo il percorso.

### 3. Passaggi Preliminari

Prima di eseguire i test, è importante seguire alcuni passaggi preliminari per garantire che i risultati siano accurati:

- **Connessione Diretta al Modem/Router**
Quando esegui il test di velocità, è importante che il dispositivo (PC, laptop, etc.) sia connesso direttamente al router o al modem via cavo Ethernet. Questo elimina variabili come la qualità del segnale Wi-Fi, che può ridurre significativamente la velocità di connessione.

- **Sospensione di altre Attività**
Assicurati che non ci siano altre applicazioni o dispositivi che utilizzano la connessione Internet mentre esegui il test. Streaming, download, giochi online e videochiamate possono influire sulla velocità e sulla qualità del test.

- **Spegnere e Riavviare il Modem/Router**
Se sospetti che ci sia un problema di connessione, un riavvio del modem o del router può risolvere molti problemi legati alla connessione.

- **Disattivare Antivirus e Firewall**
Alcuni antivirus o firewall possono interferire con i test di velocità. Disattivali temporaneamente per ottenere risultati più precisi.

### 4. Test di Velocità della Connessione

Il primo passo per testare una connessione ADSL o fibra è misurare la **velocità di download e upload**. La velocità di download indica quanto velocemente i dati possono essere scaricati dal server al tuo dispositivo, mentre la velocità di upload mostra quanto velocemente puoi caricare i dati su Internet (ad esempio, per inviare file o videochiamate).

### Come Fare un Test di Velocità

1. **Accedi a un sito di test di velocità** come [Speedtest.net](https://www.speedtest.net/) o [Fast.com](https://www.fast.com).
2. **Scegli il server di test**: Speedtest.net ti permette di scegliere un server vicino alla tua posizione geografica per ottenere misurazioni più accurate.
3. **Avvia il test**: Clicca su “Go” per avviare il test di velocità.
4. **Analizza i risultati**: Dopo pochi secondi, il test mostrerà tre valori principali:
   - **Velocità di download** (in Mbps)
   - **Velocità di upload** (in Mbps)
   - **Ping** (in millisecondi, ms)

### Cosa Significano i Risultati?

- **Velocità di Download**: Un buon valore per una connessione ADSL è tra i 5 e i 20 Mbps, mentre per la fibra ottica si può arrivare anche a 1000 Mbps (1 Gbps) o oltre.
- **Velocità di Upload**: La velocità di upload è spesso inferiore alla velocità di download, ma dovrebbe comunque essere abbastanza alta da consentire attività come l’upload di file di grandi dimensioni.
- **Ping**: Un ping basso (inferiore a 50 ms) è ideale, soprattutto per attività in tempo reale come il gaming online. Un ping più alto può indicare latenza o congestionamento nella rete.

### 5. Test di Ping e Latenza

Il **ping** misura il tempo impiegato da un pacchetto di dati per viaggiare dalla tua connessione a un server remoto e tornare indietro. È un indicatore della latenza della tua connessione.

### Come Testare il Ping

Puoi testare il ping utilizzando il comando "ping" sul tuo computer.

- **Windows e Mac**: Apri il Terminale e digita:
  ```sh
  ping www.google.com
  ```
- **Esempio del risultato ottenuto**
  ```sh
  Pinging www.google.com [137.137.137.137] with 32 bytes of data:
  Reply from 137.137.137.137: bytes=32 time=9ms TTL=118
  Reply from 137.137.137.137: bytes=32 time=9ms TTL=118
  Reply from 137.137.137.137: bytes=32 time=9ms TTL=118
  Reply from 137.137.137.137: bytes=32 time=9ms TTL=118
  Ping statistics for 137.137.137.137:
  Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
  Approximate round trip times in milli-seconds:
  Minimum = 9ms, Maximum = 9ms, Average = 9ms
  ```

### Cosa Indica il Risultato del Ping?

- **Ping basso (0-50 ms)**: Ottimo per navigazione, gaming e videochiamate.
- **Ping medio (50-100 ms)**: Adeguato per la maggior parte delle attività online, ma potrebbe esserci una leggera latenza nelle videochiamate o nel gaming.
- **Ping alto (oltre 100 ms)**: Indica un ritardo significativo, che può influire negativamente sull’esperienza di gioco o sullo streaming in tempo reale.

### 6. Test di Qualità della Connessione (Jitter e Packet Loss)

La **qualità della connessione** non dipende solo dalla velocità o dal ping, ma anche da altri fattori come il **jitter** e il **packet loss**. Questi due parametri influenzano la stabilità e la fluidità della tua connessione.

### Jitter

Il jitter misura la variazione nel ping durante il test. Un jitter elevato può causare problemi durante lo streaming video o le chiamate VoIP.

- **Basso Jitter** (inferiore a 30 ms) è ideale.
- **Alto Jitter** (oltre 50 ms) può causare interruzioni nel flusso di dati.

### Packet Loss

Il **packet loss** si verifica quando i pacchetti di dati non riescono a raggiungere la destinazione. Un alto packet loss indica una connessione instabile.

- **Nessun Packet Loss** è ideale.
- **Fino al 1% di Packet Loss** è accettabile.
- **Oltre il 1% di Packet Loss** può causare problemi significativi.

### 7. Verifica della Velocità a Casa e Comparazione con i Dati del Contratto

Una volta ottenuti i risultati del test, confrontali con la velocità promessa nel tuo contratto. Ad esempio, se hai sottoscritto un piano che offre una velocità di download di 100 Mbps, ma il tuo test mostra solo 30 Mbps, potrebbe esserci un problema nella tua connessione.

### 8. Problemi Comuni nelle Connessioni ADSL e Fibra

Alcuni dei problemi comuni che possono influenzare le tue prestazioni di rete includono:

- **Congestionamento della rete**: Se molte persone stanno utilizzando la connessione nello stesso momento, la velocità potrebbe diminuire.
- **Distanza dal router**: Una connessione Wi-Fi instabile può ridurre significativamente la velocità di internet.
- **Problemi con il modem o il router**: Dispositivi obsoleti o mal configurati possono causare problemi di connessione.

### 9. Come Risolvere i Problemi Comuni

Ecco alcune soluzioni per i problemi più comuni:

- **Riavvia il modem/router** per risolvere piccoli problemi temporanei.
- **Controlla impostazioni scheda di rete** ethernet e wireless per eliminari problemi legati alle impostazioni.
- **Utilizza una connessione cablata** per eliminare problemi legati al Wi-Fi oppure migliorare quella Wi-Fi implementato una **rete Mesh**
- **Contatta il tuo provider** per verificare se ci sono problemi di rete o di manutenzione.

### 10. Verifica della Connessione con il Provider

Se dopo aver eseguito tutti i test riscontri problemi, è utile contattare il tuo provider di servizi Internet. Fornisci i risultati dei test e chiedi loro di verificare la tua connessione. Molti provider offrono supporto tecnico per aiutarti a risolvere i problemi di velocità.

### 11. Conclusioni

Testare la tua connessione ADSL o fibra è un passo fondamentale per comprendere se stai ottenendo il servizio per cui stai pagando. I test di velocità, ping, jitter e packet loss ti forniranno una panoramica completa della qualità della tua connessione. Se rilevi problemi, segui i suggerimenti di risoluzione o contatta il tuo provider per assistenza.

Con questa guida, dovresti essere in grado di diagnosticare i problemi comuni e prendere le misure necessarie per migliorare la tua esperienza online.
