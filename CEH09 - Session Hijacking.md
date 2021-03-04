CEH09: Session Hijacking
=====

Concetti di Session Hijacking
-----
Il Session Hijacking è una metodologia di attacco nella quale l'attaccante cerca di inserirsi in una comunicazione TCP tra due computer. L'attaccante, sniffando il traffico, può compromettere la vittima con frodi, furti di identità e/o di credenziali.

#### Tipologie di Session Hijacking
**ACTIVE ATTACK**: In un attacco di questo tipo l'attaccante trova una sessione attiva e se ne impossessa.

**PASSIVE ATTACK**: In un attacco passivo invece viene sniffato e registrato il traffico.

#### Session Hijacking nel modello OSI
NETWORK LEVEL HIJACKING: Intercettazione (sniff) di pacchetti durante una trasmissione TCP/UDP tra client e server.

APPLICATION LEVEL HIJACKING: Ottenimento della user session applicativa (ad es. HTTP) tramite session ID.

Session Hijacking a livello applicativo
-----
In un attacco session hijacking, un session token deve essere rubato o predetto per poter permettere un accesso non autorizzato al web server (HTTP).

#### Compromissione di ID di sessione con attacchi client-side
*Gli XSS permettono agli attaccanti di iniettare script malevoli e farli eseguire agli altri utenti che visitano la pagina
*Un codice malevolo scritto in JS può essere incluso in una pagina web e catturare le sessioni degli utenti
*Un trojan potrebbe cambiare le impostazioni del proxy nel browser e inviare le sessioni attraverso una macchina gestita dall'attaccante

#### Session Hijacking con attacco CRIME
CRIME (Compression Ratio Info-leak Made Easy) è un attacco client-side che sfrutta le vulnerabilità presenti nei protocolli di compressione come SSL/TLS, SPDY e HTTPS.

Session Hijacking a livello network
-----
Questa tipologia di session hijacking si basa sui protocolli utilizzati dalle web application a livello applicativo, l'attaccante ottiene informazioni critiche che vengono poi utilizzate per attaccare il livello applicativo.

#### TCP/IP Hijacking
Utilizza pacchetti spoofed per impossessarsi della connessione tra vittima e target, l'attaccante deve però risiedere nella stessa network.
