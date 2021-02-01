CEH08: Denial of Service
=====

Introduzione a DoS e DDoS
-----

L'attacco DoS (Denial of Service) è un tipo di attacco che colpisce computer o reti e riduce, restringe o previene l'accesso alle risorse da parte di utenti legittimi. L'attaccante inonda la vittima con richieste non legittime o semplice traffico per sovracaricarne le risorse.

DDoS (Distributed Denial of Service) è un attacco DoS coordinato che coinvolge un numero elevato di computer zombie (sistemi compromessi in precedenza, botnet) per attaccare un singolo target.

Tecniche di attacco DoS/DDoS
-----

**VOLUMETRIC ATTACK**: Consuma la banda del target (network o servizio).

**PROTOCOL ATTACK**: Utilizza risorse come le connection state table presenti negli apparati di rete.

**APPLICATION LAYER ATTACK**: Consuma le risorse dell'applicazione (o servizio) in modo da renderlo non funzionante agli utenti legittimi.

#### UDP Flood
L'attaccante invia pacchetti UDP con indirizzo spoofed ad alta frequenza, su porte casuali. Questo comporterà che il server sarà costretto a "controllare" se esistono applicazioni che possano rispondere sulle porte selezionate.

#### SYN Flood
L'attaccante invia una massiccia quantità di richieste SYN al target con indirizzo IP sorgente fittizio, il target risponderà con SYN+ACK attendendo per l'ACK finale.
Il target non riceverà risposta in quanto l'IP sorgente è falso; un three-way handshake incompleto può rimanere in attesa fino a 75 secondi.

#### Fragmentation Attack
Questa tipologia di attacco riduce drasticamente l'abilità del target di riassemblamento pacchetti. Il target, inondato di pacchetti TCP o UDP frammentati, cercerà di riassemblarli e questo porterà ad una riduzione di performance.
I pacchetti frammentati solitamente passano attraverso i sistemi di difesa network inosservati, in quanto riassemblare e ispezionare grandi pacchetti frammentati consumerebbe una quantità eccessiva di risorse di sistema.

#### Multi-Vector Attack
L'attaccante in questo caso utilizza una combinazione di attacchi volumetrici, di protocollo e application layer. Possono essere lanciati un vettore alla volta o in parallelo per confondere gli analisti.

Tecniche di detection e mitigazione
-----

Le tecniche di detection sono basate sull'identificazione e la discriminazione del traffico malevolo (aumenti costanti di traffico o spike) e eventi circostanziati di aumento non previsto di pacchetti legittimi. Tutte le tecniche di detection definiscono un attacco come una **deviazione anormale e notevole dalle soglie prefissate** durante il normale traffico di rete.

* **ACTIVITY PROFILING**: Questo tipo di analisi studia il packet rate medio nella rete, e nei singoli segmenti, per verificare la presenza di traffico malevolo.
* **SEQUENTIAL CHANGE-POINT DETECTION**: Sono degli algoritmi che filtrano il traffico in base all'indirizzo, la porta o il protocollo e indicizzano i risultati in una scala temporale.
* **WAVELET-BASED SIGNAL ANALYSIS**: L'analisi wavelet descrive un segnale in ingresso in termini spettrali, quest'analisi permette di filtrare il traffico anomalo dal traffico normale.

#### Contromisure
**Assorbire l'attacco**: Utilizzare ulteriori risorse (banda, risorse di sistema)

**Degradare servizi**: Spegnere i servizi non critici e non necessari

**Spegnere i servizi**: Spegnere tutti i servizi finché l'attacco non è finito

#### Prevenzione
* EGRESS FILTERING: Scansionare gli header dei pacchetti IP che lasciano la rete, assicurarsi che traffico non autorizzato o malevolo lasci la rete interna.
* INGRESS FILTERING: Prevenire lo spoofing dell'indirizzo sorgente, protegge dagli attacchi flooding.
* TCP INTERCEPT: La funzionalità TCP Intercept presente nei router, protegge i server TCP da attacchi SYN Flooding. Previene attacchi DoS validando le connessioni TCP.
* RATE LIMITING: Controlla il rate del traffico in ingresso e in uscita, riduce l'alto traffico in ingresso.

#### Riflessione
Esistono sistemi che sono impostati con un basso livello di sicurezza (honeypot) e fungono da esca per gli attaccanti. Un honeypot serve a raccogliere informazioni sull'attaccante e sulle tecniche di attacco.
Utilizzare un approccio **defense-in-depth** in diversi punti della rete per dirottare il traffico sospetto DoS verso le honeypot.

#### Mitigazione
* LOAD BALANCING: Bilanciare il carico in un architettura multi-server permette di mitigare gli attacchi DDoS.
* THROTTLING: Questo metodo aiuta i router a farsi carico di un eccessivo traffico in ingresso, così da permettere ai server di poterli gestire correttamente.
* DROP REQUESTS: I server e i router cominciano a droppare pacchetti quando il carico aumenta eccessivamente.
