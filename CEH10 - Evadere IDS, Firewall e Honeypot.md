CEH10: Evadere IDS, Firewall e Honeypot
=====

Concetti generali
-----

Un IDS (Intrusion Detection System) è un software (o hardware) di sicurezza che ispeziona tutto il traffico in ingresso e in uscita dalla rete, alla ricerca di pattern sospetti.

#### Tipologie di IDS
* **NIDS**: Network based IDS, consiste in una macchina posta nella rete in modalità promiscua, in ascolto sul traffico, in grado di generare alert in caso di pattern malevoli.
* **HIDS**: Host based IDS, sono in genere applicativi (agent) installati in host specifici, in grado di fare auditing sugli eventi dell'host in analisi.

#### Firewall
Sono dispositivi hardware (o software) che prevengono gli accesso non autorizzati da e verso le reti private; sono in genere posizionati tra la rete pubblica e quella privata. Il firewall analizza tutti i pacchetti che entrano o lasciano la rete e blocca quelli che non rispettano i criteri di sicurezza impostati.

#### Architettura firewall
BASTION HOST: È un sistema configurato per proteggere le risorse dagli attacchi, ha due interfacce, una per la rete privata e una per internet.

SCREENED SUBNET: È più comune chiamarla DMZ (DeMilitarized Zone) e contiene host che offrono servizi che devono essere disponibili all'esterno (ad es. webserver), la zona privata non può essere raggiunta dagli utenti internet. 

MULTI-HOMED FIREWALL: Sono firewall con due o più interfacce che permettono un'ulteriore suddivisione della rete in base a specifiche di security dettate dall'azienda.

#### DMZ - DeMilitarized Zone
La DMZ è una rete che si utilizza come buffer tra la rete interna (sicura) e internet (insicuro). Viene creata con un firewall con tre o più interfacce di rete.

Tecniche di IDS evasion
-----

Si riduce tutto a far vedere all'IDS pacchetti che in realtà sono altro.

#### Insertion Attack
È una tipologia di attacco che confonde l'IDS facendogli leggere pacchetti non validi, l'IDS accetterà i pacchetti che saranno rifiutati dagli end system coinvolti, ciò comporterà l'inserimento di dati nell'IDS.

#### Obfuscation
È una tecnica di evasione IDS, consiste nell'encoding del pacchetto (contenente un payload) in maniera tale che sia decifrabile solo dall'host target e non dall'IDS, in genere viene utilizzata la crittografia o l'encoding Unicode.

Tecniche di firewall evasion
-----

L'identificazione dei firewall può avvenire tramite port scanning e discovery dei servizi running, firewalking che consiste nell'utilizzo del TTL per determinare le ACL e mappare la rete, e banner grabbing per il footprinting.

#### IP Address Spoofing
L'attaccante maschera il proprio indirizzo IP come se fosse un host fidato, questo avviene modificando l'header dei pacchetti IP in modo da riuscire a bypassare il firewall.

#### Bypass di siti web bloccati
Alcuni siti web permettono di navigare su altri siti web attraverso di essi, evitando così le regole IP-based del firewall.

#### Firewall bypass tramite ICMP Tunneling
Questa tecnica permette, ad esempio, di incapsulare una backdoor nella porzione di dati dei pacchetti ICMP, la parte del payload è arbitraria e non è esaminata da molti firewall pertanto è possibile incapsulare qualsiasi tipo di dato.
