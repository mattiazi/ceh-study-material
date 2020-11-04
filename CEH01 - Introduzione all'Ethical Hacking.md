CEH01: Introduzione all'Ethical Hacking
=====

Panoramica sulla sicurezza delle informazioni (Information Security)
-----

#### Terminologia
* **HACK VALUE** - Nozione che indica quanto ne vale la pena ad acquisire il target.
* **VULNERABILITY** - Esistenza di una falla, errore di implementazione o di design che può essere sfruttato da un evento inaspettato per compromettere la sicurezza di un sistema.
* **EXPLOIT** - Una breccia nella sicurezza di un sistema IT tramite una vulnerabilità.
* **PAYLOAD** - Il payload è la parte di un codice exploit che esegue attività malevole come creare una backdoor, cifrare file.
* **ZERO-DAY** - Vulnerabilità non ancora patchata dal vendor. Un attacco 0-day sfrutta questo tipo di vulnerabilità prima del rilascio della relativa patch.
* **DAISY CHAINING** - Consiste nell'accedere ad una rete e/o computer e utilizzarli per accedere ad ulteriori reti e/o computer che contengono le informazioni desiderate.
* **DOXING** - Pubblicazione di informazioni personali di un soggetto raccolte da fonti aperte (es. Social Media).
* **BOT** - Un bot è un software che può essere controllato da remoto per eseguire o automatizzare determinati task.

#### Elementi di Information Security
* **CONFIDENTIALITY** - Assicura che l'informazione sia accessibile solo ai soggetti autorizzati.
* **INTEGRITY** - L'affidabilità di dati o risorse in termini di prevenzione di modifiche improprie o non autorizzate.
* **AVAILABILITY** - Assicura che i sistemi responsabili della consegna, memorizzazione ed elaborazione delle informazioni siano accessibili quando un utente autorizzato lo richiede.
* **AUTHENTICITY** - L'autenticità si riferisce alla caratteristica di una comunicazione, documento o dati, di essere genuina.
* **NON-REPUDIATION** - Garantisce che il mittente di un messaggio non potrà negare di averlo inviato e il destinatario non potrà negare di averlo ricevuto.

Comprendere le minacce alla sicurezza delle informazioni e i vettori di attacco
-----

#### Motivi, scopi e obiettivi degli attacchi alla sicurezza delle informazioni
> ATTACCO = MOTIVO + METODO + VULNERABILITÀ

* Il motivo nasce quando il sistema target memorizza o elabora qualche informazione preziosa e questo porta alla minaccia di un attacco al sistema.
* Gli attaccanti utilizzano vari strumenti e tecniche di attacco per sfruttare le vulnerabilità in un sistema e raggiungere il proprio scopo.

I motivi dietro un attacco possono essere: rubare informazioni, manipolazione dei dati, interruzione alla business continuity, instillare paura e caos interrompendo il funzionamento di infrastrutture critiche, perdite economiche, propaganda religiosa o politica, raggiungere obiettivi governativi, rovinare la reputazione, vendetta, chiedere un riscatto.

#### Vettori di attacco più popolari
1. **CLOUD COMPUTING THREATS**
    * Il cloud computing offre risorse IT on-demand dove spesso le organizzazioni memorizzano i propri dati e quelli dei propri clienti.
    * Una falla in una cloud application di un cliente potrebbe garantire l'accesso ad un eventuale attaccante ai dati di altri clienti.
2. **ADVANCED PERSISTENT THREATS**
    * APT è un tipo di attacco il cui scopo è rubare informazioni alle vittime senza essere rilevato.
    * APT è un termine che viene utilizzato anche per identificare gruppi hacker strutturati (APT38).
3. **VIRUS E WORM**
    * I virus e I work sono le minacce più popolari e sono capaci di infettare reti e sistemi.
4. **RANSOMWARE**
    * I ransomware inibiscono l'accesso a computer o file cifrandoli e richiedendo un riscatto per il rilascio dei file.
5. **MOBILE THREATS**
    * L'aumento dell'utilizzo di device mobili (smartphone e tablet) ha fatto aumentare le minacce verso questo tipo di dispositivi che ad oggi vengono utilizzati sia per scopi personali che aziendali.

#### Tipologie di attacchi ai sistemi
|Livello||
|-----|-----|
|Sistema Operativo|L'attaccante cerca vulnerabilità nel S.O. o nella configurazione e cerca di sfruttarla per accedere al sistema. Vulnerabilità a livello del S.O.: buffer overflow, bug, patch non installate|
|Livello Applicativo|L'attaccante sfrutta vulnerabilità nelle applicazioni che vengono eseguite nei sistemi delle organizzazioni per accedere ai sistemi e rubare i dati o manipolarli. Attacchi: buffer overflow, XSS, SQL Injection, man-in-the-middle, session hijacking, DoS|
|Misconfiguration|Le vulnerabilità dovute a misconfiguration colpiscono principalmente web server, database, reti o possono essere dovute all'utilizzo di framework|
|Shrink-Wrap Code|L'attaccante sfrutta le configurazioni e le impostazioni di default dei sistemi (o del codice) presenti nell'infrastruttura|

Panoramica sui concetti di hacking, tipologie e fasi
-----

L'hacking è l'abilità di sfruttare le vulnerabilità di un sistema e compromettere i controlli di sicurezza per accedere alle risorse, può includere modifiche al sistema o alle feature delle applicazioni.

#### Chi è un hacker
1. Ottime competenze informatiche
2. Per alcuni hacker può essere solo un hobby
3. Le intenzioni possono essere semplice curiosità per accrescere la propria conoscenza o fare qualcosa di illegale

* *Blackhat* - Hacker malevolo. L'intenzione è quella di fare qualcosa di illegale o arrecare danno.
* *Greyhat* - Un hacker che sta da ambo le parti. L'intenzione può essere malevola o no.
* *Whitehat* - Un hacker "bravo ragazzo". Aiuta le organizzazioni a mettere in sicurezza i propri sistemi.
* *Hacktivist* - Ha uno scopo politico.
* *State sponsored hacker* - Sono hacker ingaggiati da governi per penetrare altri governi.
* *Cyber Terrorists" - Sono motivati da un credo religioso o politico.
* *Suicide Hacker* - Un hacker a cui non interessa finire in carcere o ricevere punizioni (multe).
* *Script Kiddies* - Un hacker con basse conoscenze tecniche che utilizza strumenti sviluppati da altri.

#### Fasi dell'hacking
1. **Reconnaissance**
    * PASSIVE RECON: senza interazione con il target.
    * ACTIVE RECON: con interazione diretta con il target.
2. **Scanning**
    * PRE-ATTACK PHASE: Si effettua uno scan della rete alla ricerca di informazioni specifiche in base alle informazioni ottenute durante la fase precedente.
    * PORT SCANNER: Si utilizzano strumenti come port scanner, vulnerability scanner e network mapper.
    * EXTRACT INFORMATION: L'attaccante estrae informazioni quali le macchine attive e lo stato delle porte.
3. **Gaining Access**
    * Fa riferimento all'ottenimento dell'accesso ad un OS o applicazione.
    * L'attaccante può accedere al sistema operativo tramite il livello applicativo o il livello network.
    * L'attaccante cerca di scalare i propri privilegi per ottenere il controllo completo del sistema.
    * Vengono effettuati password cracking, sfruttati buffer overflow, session hijacking e DoS.
4. **Maintaining Access**
    * L'attaccante cerca di mantenere il controllo del sistema.
    * L'attaccante si assicura di mettere in sicurezza il proprio accesso privilegiato con backdoor, rootkit o trojan.
    * L'attaccante può manipolare i dati, le applicazioni e le configurazioni del sistema.
    * L'attaccante utilizza il sistema compromesso per lanciare ulteriori attacchi.
5. **Clearing Tracks**
    * Vengono nascoste le tracce dell'intrusione o dell'attacco.
    * L'accesso ottenuto rimane nascosto.
    * Vengono sovrascritti i log per eliminare i sospetti.

Concetti e scopi dell'Ethical Hacking
-----

#### Cos'è l'Ethical Hacking
L'Ethical Hacking coinvolge strumenti e tecniche per identificare le vulnerabilità, si basa su tecniche che simulano il comportamento di un attaccante per verificare la possibilità di sfruttare tali vulnerabilità. Gli Ethical Hacker lavorano esclusivamente con il permesso del cliente (target).

#### Perché l'Ethical Hacking è necessario
> Per sconfiggere un hacker devi pensare come tale!

L'Ethical Hacking previene che gli hacker possano accedere ai nostri sistemi, ci rende coscienti delle vulnerabilità presenti, migliora la sicurezza informatica delle aziende, evita eventuali violazioni, salvaguarda i dati dei clienti e aumenta la *security awareness*.

Un Ethical Hacker dovrebbe farsi queste domande:

* Cosa può vedere un attaccante nel sistema target?
* Cosa può fare con queste informazioni?
* Qualcuno noterebbe i tentativi di intrusione al sistema target?
* Sono protette tutte le componenti del sistema?
* Quanto sforzo è necessario per ottenere una protezione adeguata?
* Le misure di sicurezza adottate sono conformi con gli standard legali e industriali?

Controlli per la sicurezza delle informazioni
-----

#### Garanzia dell'informazione
La garanzia dell'informazione fa riferimento alla garanzia che l'integrità (*integrity*), disponibilità (*availability*), riservatezza (*confidentiality*) e l'autenticità (*authenticity*) dell'informazione e dei sistemi informatici sia protetta durante l'utilizzo, l'elaborazione, la memorizzazione e la trasmissione delle informazioni.

#### Information Security Management Program
Sono programmi che abilitano le organizzazioni e le aziende ad operare in uno stato dove il rischio è ridotto, comprende tutti i processi organizzativi e operativi e i partecipanti rilevanti per la sicurezza delle informazioni.
È una combinazione di policy, processi, procedure, standard e linee guida per stabilire il livello richiesto per la sicurezza delle informazioni.

#### Enterprise Information Security Architecture (EISA)
EISA fa riferimento ad un insieme di requisiti, processi, principi e modelli che determinano la struttura e il comportamento dei sistemi informatici delle organizzazioni.

#### Segregazione delle reti
Il "Network Security Zoning" aiuta a monitorare e controllare il traffico in entrata e uscita. Inoltre aiuta le organizzazioni a gestire le proprie reti sicure selezionando il giusto livello di sicurezza in base alle differenti zone delle reti internet e intranet.

#### Policy per l'Information Security
Le policy sono il fondamento dell'infrastruttura di sicurezza e definiscono i requisiti minimi di sicurezza e le regole per permettere una corretta protezione dei sistemi.

#### Tipologie di policy
* **PROMISCUOUS POLICY** - Nessuna restrizione per l'utilizzo dei sistemi e delle relative risorse.
* **PERMISSIVE POLICY** - È una policy piuttosto permissiva, blocca soltanto i comportamenti che potrebbero arrecare danno, deve essere aggiornata regolarmente.
* **PRUDENT POLICY** - Fornisce un livello di sicurezza elevato, blocca tutti i servizi esclusi quelli necessari e/o riconosciuti, tutti i movimenti vengono tracciati.
* **PARANOID POLICY** - Questa policy blocca tutto.

#### Progettare le policy di sicurezza
1. Identificare i rischi tramite un Risk Assessment
2. Imparare dagli altri e dalle linee guida
3. Includere il management nello sviluppo delle policy
4. Ammende/Multe chiare in caso di mancata conformità
5. Fornire la versione finale della policy a tutti
6. Assicurarsi che tutti abbiano capito la policy
7. Sviluppare strumenti per rinforzare le policy
8. Formare i dipendenti
9. Rivedi e aggiorna regolarmente le policy

#### Sicurezza fisica

#### Cos'è il rischio

#### Risk Management

#### Incident Management
**Incident Management Process**
1. Preparation for Incident Handling and Response
2. Detection and Analysis
3. Classification and Prioritization
4. Notification
5. Containment
6. Forensic Investigation
7. Eradication and Recovery
8. Post-Incident Activities
