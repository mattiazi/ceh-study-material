CEH07: Sniffing
=====

Concetti di sniffing
-----

####Network Sniffing
Il packet sniffing è un processo di monitoraggio e di cattura di tutti i pacchetti che transitano in una rete tramite l'utilizzo di un software o di hardware apposito.

####Tipologie di Sniffing
**PASSIVE SNIFFING**: si riferisce ad una tecnica di sniffing attraverso hub (che non sono più in utilizzo oggi) e può essere effettuata solo in una rete dove i pacchetti sono inviati a tutti i dispositivi.
**ACTIVE SNIFFING**:  è una tecnica che si utilizza in una rete dove ci sono degli switch, consiste nell'iniettare pacchetti ARP nella rete per riempire la CAM (content addressable memory) dello switch. Le tecniche utilizzate includono: MAC flooding, Attacchi DHCP, DNS Poisoning, Switch Port Stealing, ARP Poisoning e attacchi spoofing. Il NIC deve essere in modalità promiscua.

Attacchi MAC
-----

Quando la CAM di uno switch è piena, i pacchetti vengono inviati a tutte le porte dello switch, trasformandolo di fatto in un hub. La modalità dello switch viene resettata in "learning mode". In genere la CAM viene riempita con IP/MAC fittizi.

####Switch Port Stealing
Questa tecnica utilizza il MAC Flooding per sniffare i pacchetti. L'attaccante inonda lo switch con pacchetti ARP appositamente modificat: il pacchetto infatti ha il MAC del target come sorgente e il MAC dell'attaccante come destinatario; se l'attaccante è abbastanza veloce rispetto allo switch allora i pacchetti verranno redirezionati verso di lui e non più al target legittimo.

Attacchi DHCP
-----

I server DHCP mantegono le configurazioni TCP/IP in un database come parametri validi.

####Attacco DHCP Starvation
Questa tipologia di attacco è un DoS verso il DHCP server. L'attaccante effettua il broadcast di richieste DHCP e fa in modo di farsi "rilasciare" degli indirizzi IP, questo inibisce l'utente ad ottenere o rinnovare il proprio indirizzo IP.

####Rouge DHCP Server
L'attaccante abilita un server DHCP fittizio nella rete per rispondere alle richieste DHCP, questo attacco viene utilizzato con l'aiuto del DHCP Starvation: l'attaccante invia configurazioni TCP/IP agli utenti che ne fanno richiesta dopo aver delegittimato il server DHCP genuino.

ARP Poisoning
-----

Il protocollo ARP è **stateless** e viene usato per mappare gli IP e i MAC dei dispositivi. Tutti i dispositivi infatti, effettuano richieste ARP in broadcast per trovare il MAC di un apparato. Con ARP è possibile inviare risposte anche se non è stata effettuata una richiesta specifica, quindi in una rete è possibile, prima che qualche dispositivo lo chieda, effettuare una richiesta del tipo "Ciao io sono A e ho il MAC XX:XX:XX", il target registrerà comunque l'informazione.

####Minacce
Utilizzando richieste ARP fittizie un attaccante può introdursi nella comunicazione tra due host risultando di fatto in un man-in-the-middle.

* Packet sniffing
* Session Hijacking
* VOIP Call Tapping
* Manipolazione dei dati
* Attacchi MITM
* Intercettazioni di dati
* Connection Hijacking
* Connection reset
* Furto di credenziali
* Attacchi DoS

DNS Poisoning
-----
Il DNS Poisoning è una tecnica che imbroglia un server DNS e lo induce a credere che ha ricevuto un'informazione autentica, infatti vengono inseriti degli indirizzi IP sbagliati/falsi nella configurazione DNS che si occupa della traduzione degli indirizzi web in IP.

####Intranet DNS Spoofing
Il sistema dell'attaccante deve essere connesso alla rete LAN e abilitato allo sniff dei pacchetti, funziona molto bene contro switch con ARP Poisoning routing.

####Host File
Modificare il file hosts del sistema permette all'attaccante un notevole successo: infatti se il sistema trova la query cercata nel proprio file hosts non andrà a chiederla al server DNS.

####Proxy Server DNS Poisoning
Un attaccante può cambiare le impostazioni del proxy server della vittima e tutte le richieste passeranno non dal proxy originario ma da quello impostato dall'attaccante

####DNS Cache Poisoning
Questa tipologia di attacco consiste nell'alterazione della cache DNS (o nell'aggiunta di record DNS) nella cache del resolver DNS in modo da redirezionare il traffico verso siti malevoli.
