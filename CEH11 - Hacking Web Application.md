CEH11: Hacking Web Application
=====

Concetti generali
-----

Le applicazioni Web forniscono un'interfaccia tra utente finale e web server, attraverso una serie di pagine web generate dinamicamente (o statiche) che vengono servite dal web server.

Minacce alle Web Application
-----

#### OWASP Top 10 Application Security Risks (2017)
1. Injection
2. Broken Authentication
3. Sensitive Data Exposure
4. XML External Entity
5. Broken Access Control
6. Security Misconfiguration
7. Cross-Site Scripting (XSS)
8. Insecure Deserialization
9. Componenti con vulnerabilità note
10. Logging e monitoraggio insufficiente

#### Injection
È una vulnerabilità che permette a dati non validati di essere interpretati ed eseguiti dal server, si suddividono in: SQL Injection, Command Injection, LDAP Injection.

#### Broken Authentication
Un attaccante può sfruttare le vulnerabilità presenti nel meccanismo di autenticazione o nelle funzioni che gestiscono le sessioni come: account esposti, session ID, logout, password management, timeouts, domande di sicurezza e altro per impersonificare un utente.

#### Sensitive Data Exposure
Molte applicazioni web non proteggono le informazioni sensibili da accessi non autorizzati, questo si può verificare se vi sono falle come una scorretta gestione della cifratura o leak di informazioni (ad es. accessi).

#### XXE - XML External Entity
È un attacco server-side, nello specifico un SSRF (Server-Side Request Forgery), dove l'applicazione effettua il parsing di un file XML da una sorgente non riconosciuta. Sfrutta gli errori del parser XML.

#### Broken Access Control
L'Access Control si riferisce a come una web application permette l'accesso ai propri contenuti e funzioni, questo metodo bypassa l'autenticazione.

#### Security Misconfiguration
Un attaccante che utilizza una vulnerabilità dovuta a misconfiguration (come utilizzare gli account di default o gestire file non protetti) potrà avere accesso non autorizzato al sistema. In genere viene sfruttato utilizzando input non validati, form tampering, scorretta gestione degli errori e delle eccezioni o misure di sicurezza insufficiente a livello di trasporto.

#### XSS - Cross-Site Scripting
L'attacco XSS sfrutta le vulnerabilità di pagine dimatiche, esso permette all'attaccante di iniettare codice all'interno delle pagine web e farlo eseguire/visualizzare ad altri utenti.

#### Insecure Deserialization
La Data Serialization/Deserialization è un processo che permette la linearizzazione di oggetti di dati in modo da poterli trasportare verso altri sistemi o altre reti, l'attaccante inietta codice malevolo e lo inoltra alla vittima.

#### Utilizzo di componenti con vulnerabilità note
Le componenti esterne, come librerie e framework, che vengono spesso utilizzate nelle webapp che vengono eseguite con determinati privilegi, una falla in un qualsiasi componente esterno può compromettere l'intera applicazione e avere un impatto molto serio. Un attaccante riesce ad identificare i componenti e le dipendenze deboli tramite scanning o analisi manuale.

#### Logging e monitoraggio insufficiente
Questo scenario si verifica quando l'applicazione non effettua un logging completo ed esaustivo o i sistemi di detection non rilevano nessuna attività malevola (o la ignorano completamente).

#### CSRF - Cross-Site Request Forgery
Un attacco CSRF sfrutta le vulnerabilità di una pagina web e permette all'attaccante di forzare il browser di un utente ad inviare richieste malevole. La vittima ha una sessione attiva con un sito web fidato e contemporaneamente visita un sito web fraudolento che inietta una richiesta HTTP verso il sito fidato, compromettendone l'integrità.

Metodologia di Web Application Hacking
-----

#### Footprinting dell'infrastruttura Web
Il footprinting è il primo step per l'hacking di webapp e consiste nell'identificazione di applicazioni vulnerabili e nella selezione delle vittime.

**SERVER DISCOVERY**: Catalogazione di informazioni sulla location dei server e sul loro stato. Informazioni su indirizzi IP, nomi DNS e port scanning permettono di svolgere la fase di service discovery in maniera più agile.
**SERVICE DISCOVERY**: Analizzare il target per identificare le porte in utilizzo. Alcuni tool per effettuare questo tipo di analisi: nmap, netscan tools pro, sandcat.
**SERVER IDENTIFICATION**: Analizzare l'header delle risposte del server per identificare modello e versione del software web server, in sostanza si tratta di banner grabbing.
**HIDDEN CONTENT DISCOVERY**: Scoprire contenuti e funzionalità nascoste che non sono raggiungibili direttamente, in modo da poterle sfruttare. (Web dir brute forcing, web spidering)

#### Detection di WAF e Proxy
PROXY: Permette di scoprire se il target sta redirezionando le richieste attraverso un proxy server, in genere questi server aggiungono alcuni campi nell'header di risposta. È possibile utilizzare il metodo TRACE (HTTP 1.1) per idetificare dei cambiamenti.

WAF: Verificare se la web application in analisi è protetta da un WAF (Web Application Firewall) tramite i cookie nelle risposte (spesso i WAF aggiungono cookie propri alla richiesta di risposta). Utilizzare **wafw00f** per scoprire che tipologia di WAF è presente.
