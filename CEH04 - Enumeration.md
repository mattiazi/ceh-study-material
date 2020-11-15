CEH04: Enumeration
=====

Panoramica
-----

Nella fase di *enumeration* l'attaccante crea delle connessioni con il sistema per eseguire query e recuperare informazioni direttamente da esso.

#### Informazioni estraibili
Risorse di rete, share, routing table, impostazioni dei servizi, dettagli su FQDN e SNMP, hostname, utenti, gruppi, applicazioni e banner.

#### Tecniche di Enumeration
* Estrarre username tramite indirizzi email
* Estrarre informazioni tramite password di default
* Estrarre username tramite SNMP
* Brute force verso Active Directory
* Estrarre i gruppi di utenti da Windows
* Estrarre informazioni tramite DNS

#### Servizi e porte
* **TCP/UDP 53**: DNS Zone Transfer
* **TCP/UDP 135**: Microsoft RPC Endpoint Mapper
* **UDP 137**: NetBIOS Name Service (NBNS)
* **TCP 139**: NetBIOS Session Service (SMB over NetBIOS)
* **TCP/UDP 445**: SMB over TCP (Direct Host)
* **UDP 161**: Simple Network Management Protocol (SNMP)
* **TCP/UDP 389**: Lightweight Directory Access Protocol (LDAP)
* **TCP/UDP 3268**: Global Catalog Service
* **TCP 25**: Simple Mail Transfer Protocol (SMTP)
* **TCP/UDP 162**: SNMP Trap

NetBIOS Enumeration
-----

I nomi NetBIOS sono stringhe di 16 caratteri ASCII usati per identificare i device, i primi 15 caratteri sono usati per il nome del device, il 16esimo è riservato per il servizio o la tipologia di name record.
**NBTSTAT** è un programma Windows che mostra le statistiche NetBIOS, le name table (locali e remote) e la cache dei nomi NetBIOS.
La risoluzione dei nomi NetBIOS non è supportata su IPv6.

#### Comandi nbtstat
* Eseguire `nbtstat.exe -c` per ottenere il contenuto della cache dei nomi NetBIOS, la name table e gli indirizzi IP risolti.
* Eseguire `nbtstat.exe -a <IP host remoto>` per ottenere la name table NetBIOS di un host remoto.

#### Tool
* SuperScan
* Hyena
* Winfingerprint
* NetBIOS Enumerator
* Nsauditor Network Security Auditor
* enum4linux

SNMP Enumeration
-----

Il protocollo SNMP (Simple Network Management Protocol) è molto utilizzato per il monitoraggio (network), con questo protocollo si possono collezionare un notevole numero di informazioni sul target come utenti, servizi in esecuzione, device connessi, configurazioni e in alcuni casi è anche possibile gestirli direttamente tramite SNMP.

#### Tool
* SNMPScanner
* OpUtils 5
* SNScan
* Engineer's Toolset (solarwind)

LDAP Enumeration
-----

Il protocollo LDAP (Lightweight Directory Access Protocol) è un protocollo per l'interrogazione e la modifica dei servizi di directory, come Active Directory (AD), o più in generale qualsiasi raggruppamento di informazioni che può essere espresso come record di dati e organizzato in modo gerarchico. LDAP opera sulla porta TCP/389, per effettuare enumeration serve un accesso al sistema da interrogare.
È possibile estrarre username, informazioni di dominio, indirizzi e la struttura organizzativa.

#### Tool
* Softerra
* JXplorer
* LDAP Admin Tool

NTP Enumeration
-----

NTP (Network Time Protocol) è il protocollo responsabile della sincronizzazione dell'orario dei sistemi, utilizza la porta 123 UDP.
Un attaccante può effettuare query al server NTP per conoscere quali sono gli host connessi ad esso, gli indirizzi IP di una rete, gli hostname e i sistemi operativi.

#### Comandi per NTP Enumeration
* ntptrace
* ntpdc
* ntpq
