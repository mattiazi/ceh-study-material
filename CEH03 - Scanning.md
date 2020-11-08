CEH03: Scanning
=====

Panoramica
-----

Il network scanning è l'insieme di procedure atte ad identificare host, porte e servizi di un sistema, viene usato per creare un profilo del target.

#### TCP Flag
* **URG** - Indica che il contenuto del pacchetto ha carattere di urgenza e quindi necessita un'elaborazione immediata.
* **PSH** - Chiede di inviare immediatamente i dati bufferizzati.
* **FIN** - Indica che non ci saranno più trasmissioni.
* **ACK** - Indica la ricezione del pacchetto.
* **RST** - Resetta la connessione.
* **SYN** - Inizializza la connessione tra 2 host.

![TCP Header](/images/ceh03_tcp_header.png)

#### TCP/IP Handshake (three-way handshake)
SYN -> SYN+ACK -> ACK

![TCP Three-way Handshake](/images/ceh03_tcp_handshake.png)

#### TCP/IP - Session Termination
FIN -> ACK & FIN -> ACK

![TCP Session Termination](/images/ceh03_tcp_termination.png)

#### Pacchetti custom
Esistono numerosi tool che permettono la personalizzazione dei flag dei pacchetti, nmap effettua questa operazione con alcuni argomenti specifici, mentre un packet crafter per windows è *COLASOFT PACKET BUILDER*.
La customizzazione dei pacchetti permette di eseguire determinati tipi di attacchi e di fare evasion di firewall e IDS.

Tool per scanning
-----

**NMAP** - È tra gli strumenti più utilizzati per il network scanning, è in grado di effettuare il discovery degli host attivi, porte aperte/chiuse/filtrate e servizi. Si può utilizzare sia via CLI che via GUI con Zenmap.

**HPING** - Generatore e analizzatore di pacchetti, il funzionamento è simile al comando ping, tuttavia con hping è possibile utilizzare protocolli diversi da ICMP e customizzare le parti del pacchetto IP.

**AMAP** - Next-generation scanning tool. Identifica applicazioni in ascolto sulle porte anche se il servizio non gira sulla porta di default.

Tecniche di scanning
-----

![Tecniche di scanning](/images/ceh03_scanning_techniques.png)

#### Inverse TCP Flag Scanning
Viene inviato un pacchetto TCP con i flag FIN, URG, PSH impostati (oppure senza flag), se il target risponde (RST/ACK) la porta è chiusa, in caso non rispondesse allora la porta è aperta.

#### ACK Flag Probe Scanning
Questa tipologia di scan è effettuabile in due modi:
* TTL based - Se il TTL del pacchetto RST è minore di 64 la porta è **aperta**
* Window based - Se il valore della window del pacchetto RST è diverso da 0 (zero), allora la porta è **aperta**

Questa tecnica viene anche utilizzata per stabilire se una porta è filtrata o meno: l'attaccante invia un pacchetto ACK con un *sequence number* casuale, se non riceve risposta allora la porta è **filtrata** (quindi c'è un firewall), altrimenti non è filtrata ricevendo un pacchetto RST.

#### IDLE/IPID Header Scan
Ogni pacchetto IP ha un numero identificativo (IPID) per il frammento in questione, il sistema operativo si occupa di aumentare il IPID per ogni pacchetto inviato. 

![IDLE Scan](/images/ceh03_idle_scan.png)

#### UDP Scanning
Nel protocollo UDP non esiste il *three-way handshake* e il target non invierà una risposta se la porta è aperta. Nel caso in cui un pacchetto UDP fosse inviato ad una porta chiusa, il target invierebbe un pacchetto *ICMP Port Unreachable* al mittente. Le porte UDP sono in genere molto utilizzate anche da spyware, trojan e altri malware.

PORTA **APERTA**
UDP -> no response

PORTA **CHIUSA**
UDP -> ICMP PORT UNREACHABLE

Tecniche di Scanning con evasione IDS/Firewall
-----

#### Tecniche di evasione IDS/Firewall
* **PACKET FRAGMENTATION** - Vengono inviati dei pacchetti frammentati che solo il destinatario riassemblerà.
* **SOURCE ROUTING** - Si specifica il percorso di routing che il pacchetto modificato dovrà fare per raggiungere il target.
* **IP ADDRESS DECOY** - I pacchetti generati useranno un indirizzo IP "esca" in modo da rendere più difficile al IDS/firewall risalire al reale mittente. I pacchetti di risposta arrivano a tutti gli IP "utilizzati".
* **IP ADDRESS SPOOFING** - Viene cambiato l'indirizzo IP del mittente così da far sembrare che il pacchetto provenga da qualcun altro. I pacchetti di risposta arrivano all'indirizzo spoofed.
* **PROXY SERVER** - Viene utilizzata una catena di proxy server per nascondere la reale provenienza di uno scan ed evadere alcuni controlli degli IDS/firewall.

Banner grabbing
-----

Il banner grabbing può essere passivo o attivo, è il metodo utilizzato per determinare il sistema operativo del target o le versioni dei servizi esposti.

#### Identificazione OS target
L'identificazione del Sistema Operativo in uso dal target fornisce un aiuto per l'individuazione di vulnerabilità da poter sfruttare. Un attaccante può identificare il sistema operativo di un target in base al TTL o alla WINDOW SIZE del pacchetto TCP, infatti lo stack tcp/ip viene implementato in maniera diversa su ogni OS. Messaggi di errore sono altrettanto utili per l'identificazione.

#### Contromisure per il banner grabbing
* Modificare i banner originali con banner fasulli 
* Spegnere i servizi non necessari per limitare le informazioni che il nostro sistema può fornire ad un attaccante
* Nascondere le estensioni dei file per nascondere le tecnologie in uso (web server)
