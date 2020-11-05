CEH02: Footprinting e Reconnaissance
=====

Concetti di Footprinting
-----

#### Cos'è il Footprinting
Il footprinting è la prima fase di ogni attacco, mira ad acquisire quante più informazioni sulla rete target in modo da identificare le possibili strade da percorrere per introdursi nel sistema.
Le tipologie di footprinting si dividono in 2 categorie: Passive (non c'è interazione con il target) e Active (interazione diretta con il target).
È possibile ottenere informazioni riguardanti l'azienda e la sua organizzazione interna, la rete aziendale e i sistemi utilizzati.

#### Obiettivi del Footprinting

|Obiettivo||
|---|---|
|CONOSCERE LA "SECURITY POSTURE"|Permette all'attaccante di conoscere la "security posture" del target in modo da avere un quadro più ampio su di esso|
|RIDURRE L'AREA|L'attaccante riduce l'area ad uno specifico range di ip, reti, domini e accessi remoti|
|IDENTIFICARE LE VULNERABILITÀ|Permette di identificare le vulnerabilità nei sistemi target così da scegliere gli exploit appropriati|
|TRACCIARE UNA MAPPA DELLA RETE|L'attaccante disegna una mappa della rete del target per conoscere l'ambiente in cui dovrà operare|

Footprinting tramite motori di ricerca
-----

Gli attaccanti utilizzano i motori di ricerca per estrarre informazioni sui propri target tra cui: piattaforme tecnologiche in uso, dettagli sui dipendenti e pagine di login.

#### Footprinting utilizzando tecniche avanzate di Google Hacking
Questa tecnica permette di fare ricerche avanzate con Google, utilizzando operatori per creare query più complesse in modo da ottenere informazioni nascoste, che possano aiutare l'attaccante a trovare vulnerabilità.

**CACHE**: Mostra le pagine salvate nella cache di Google (vecchie versioni dei risultati)

**LINK**: Elenca solo i risultati che hanno collegamenti con la pagina specificata

**LOCATION**: Trova informazioni per una location specifica

**FILETYPE**: Ricerca solo determinati tipi di file

#### Google Hacking Database
GHDB è una fonte indispensabile per ricerche ancora più ampie rispetto alle semplici ricerche su Google, infatti è un archivio pubblico di exploit e software vulnerabili. Noto anche con il nome di exploit-db.

Footprinting tramite servizi web
-----

#### Trovare TLD e sottodomini
Per ricercare i Top Level Domain e sottodomini di un'azienda si possono utilizzare servizi online come netcraft.com, mentre tool come *sublist3r* (script python) servono ad enumerare i sottodomini che a loro volta possono dare informazioni sulla struttura interna delle aziende.

#### Trovare la posizione geografica del target
Un attaccante può utilizzare Google Earth/Maps per avere la posizione geografica del target, è utile quando si vuole effettuare un attacco social engineering. Spesso le informazioni circa la localizzazione non sono precise.

#### Information Gathering con LinkedIn
InSpy è un tool che permette l'enumerazione su LinkedIn e ha due funzionalità: *TECHSPY* che permette di analizzare le job description alla ricerca delle tecnologie utilizzate, *EMPSPY* invece analizza i dipendenti.

#### Determinare il sistema operativo
La determinazione del Sistema Operativo in utilizzo è essenziale quando vogliamo lanciare un attacco; alcuni tool indispensabili sono **netcraft**, **shodan** che è un motore di ricerca per qualsiasi device connesso alla rete e **censys** che permette di approfondire la superficie d'attacco conoscendo quali host sono in rete.

Tecniche di Footprinting per siti web
-----

Il footprinting per siti web è inteso come il monitoraggio e l'analisi dei siti web del nostro target. Strumenti come **BURP SUITE**, **ZAPROXY** o altri tool servono a carpire gli header, fondamentali per l'analisi del codice HTML e dei cookie.

#### Web spiders
I web spider sono software che effettuano ricerche automatiche sul target in oggetto. Le informazioni che raccolgono possono essere utilizzate per ulteriori fasi di footprinting e attacchi di social engineering. Uno dei tool per lo spidering è **WEBDATA EXTRACTOR**.

#### Mirroring
È una tecnica che consente di copiare interamente un sito web in locale per un'analisi asincrona e offline.

#### Archive.org
Un attaccante utilizza archive.org per recuperare le vecchie versioni dei siti web che non sono più online, il funzionamento è simile a quello della cache di Google, ma archive.org contiene più istantanee temporali.

#### Estrarre metadati da documenti pubblici
L'estrazione dei metadati da documenti pubblici può essere utile per ricavare informazioni come i dati personali dei dipendenti così da eseguire ulteriori attacchi (phishing, social engineering).

Tecniche di email Footprinting
-----

#### Tracciamento email
È una tecnica utilizzata per monitorare la consegna delle email al destinatario indicato e può essere utilizzata per raccogliere informazioni sul target. Con una email HTML è possibile rilevare informazioni come indirizzi IP, mail server e posizione geografica. Alcuni strumenti sono **POLITEMAIL**, **YESWARE**, **CONTACTMONKEY** e **READNOTIFY**.

Tecniche di Competitive Intelligence
-----

#### Competitive Intelligence Gathering
Il *Competitive Intelligence Gathering* è il processo di identificazione, raccolta e analisi delle informazioni sui tuoi competitor, è un processo passivo.

#### Tracciare la reputazione online del target
Online Reputation Management (ORM) è un processo di monitoraggio della reputazione online di un'azienda (o soggetto in generale). Le recensioni negative sono, in genere, le più utili in quanto un utente arrabbiato tende ad essere più dettagliato: un eventuale attaccante potrebbe usare queste informazioni per un attacco di tipo social engineering.

Whois e DNS Footprinting
-----

#### WHOIS
I database *WHOIS* sono mantenuti dai RIR (Regional Internet Registries) e contengono le informazioni personali dei proprietari dei domini: dettagli sul dominio, informazioni di contatto del proprietario, name server, data di scadenza e di creazione.

Lista RIR:

* ARIN - America
* AFRINIC - Africa
* RIPENCC - Europe
* LACNIC - America Latina e America centrale
* APNIC - Asia (pacifico)

#### DNS
Un attaccante può determinare, tramite DNS, quali host hanno un ruolo importante nella rete per eseguire attacchi più complessi.

|Tipo Record|Descrizione|
|---|---|
|A|Punta all'indirizzo IP dell'host|
|MX|Punta al mail server del dominio|
|NS|Punta al name server del dominio|
|CNAME|Canonical Name - Permette l'utilizzo di alias per un host|
|SOA|Indica l'authority del dominio|
|SRV|Service record|
|PTR|Mappa l'IP all'hostname|
|RP|Responsible Person|
|HINFO|Host Information record - Include il tipo di CPU e il Sistema Operativo|
|TXT|Record di dati non strutturati|

Network Footprinting
-----

#### Traceroute

