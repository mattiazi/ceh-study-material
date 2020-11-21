CEH05: System Hacking
=====

Panoramica
-----

**HACKING STAGE:**

1. Gaining Access
2. Escalating Privileges
3. Executing Applications
4. Hiding Files
5. Covering Tracks

Vulnerability Assessment
-----

È il processo di discovery delle vulnerabilità e delle falle di progettazione, le vulnerabilità sono classificate per gravità e possibilità di exploit. È l'analisi delle abilità di un sistema o applicazione di resistere ad un attacco: riconosce, classifica e misura le vulnerabilità in un sistema, rete o canale di comunicazione.
Un **VA** viene spesso effettuato con tool automatici che producono un report, successivamente rivisto e approfondito dall'analista.

#### Tipologie di VA
* **ACTIVE ASSESSMENT** - Si utilizza un network scanner per trovare host, servizi e vulnerabilità.
* **PASSIVE ASSESSMENT** - Una tecnica che tramite lo sniffing di rete riesce a trovare sistemi, servizi di rete, applicazioni e vulnerabilità.
* **EXTERNAL ASSESSMENT** - L'assessment viene effettuato dal punto di vista dell'attaccante (esternamente) per verificare quali vulnerabilità è possibile sfruttare.
* **INTERNAL ASSESSMENT** - Uno scan all'interno dell'infrastruttura per trovare vulnerabilità da sfruttare.
* **HOST-BASED ASSESSMENT** - Determina le vulnerabilità di uno specifico sistema (server, workstation), implica assessment alle configurazioni di sistema.
* **NETWORK ASSESSMENT** - Verifica che tipo di attacchi network sono possibili alla rete in analisi.
* **APPLICATION ASSESSMENT** - Testa l'infrastruttura web del target alla ricerca di misconfiguration o vulnerabilità note.
* **WIRELESS NETWORK ASSESSMENT** - Viene effettuato sulla rete wireless del target alla ricerca di vulnerabilità da sfruttare.

Tecniche di Password Cracking
-----

* **DICTIONARY ATTACK** - Un file dizionario viene usato dall'applicazione di cracking per accedere all'account target.
* **BRUTE FORCE ATTACK** - Il programma di password cracking prova tutte le combinazioni di caratteri finché non riesce a trovare quella giusta per accedere all'account.
* **RULE BASE ATTACK** - Questa tipologia di attacco viene privilegiata quando si ha a disposizione qualche informazione aggiuntiva sulla password da crackare.

Molto spesso nei dispositivi rimangono le password di default lasciate dai produttori (perché l'utente non sempre le cambia) e ciò permette di indovinare la password molto più semplicemente. È possibile rubare le password anche tramite trojan o spyware installati nei dispositivi della vittima.

#### Hash Injection Attack
Questo tipo di attacco permette ad un attaccante di iniettare l'hash compromesso in una sessione e sfruttarlo per accedere alle risorse di rete come se fosse il legittimo proprietario.

Tecniche di Privilege Escalation
-----

Un attaccante in genere accede ad un sistema tramite un account non amministrativo e di conseguenza diventa necessario tentare di arrivare ad un account admin. Gli attacchi privilege escalation sfruttano errori nel design delle applicazioni, errori di programmazione, bug e misconfiguration.

#### Privilege Escalation tramite DLL hijacking
La maggior parte delle applicazioni Windows non utilizza un path assoluto quando deve caricare una DLL esterna, questo permette ad un attaccante di scambiare la DLL originale con una DLL infetta, rendendo l'applicazione vulnerabile e sfruttabile per ulteriori attacchi.

#### Privilege Escalation tramite vulnerabilità
Quando si fa exploiting di una vulnerabilità, i comandi vengono spesso eseguiti con privilegi più alti, permettendo ad un attaccante di accedere ad un account admin tramite essi.

#### Altre tecniche di Privilege Escalation
* ACCESS TOKEN MANIPULATION
* APPLICATION SHIMMING
* DEBOLEZZE NEI PERMESSI DEL FILE SYSTEM
* PATH INTERCEPTION
* SCHEDULED TASK

#### Contromisure
1. Restringere i privilegi per login *interactive*
2. Utilizzare la crittografia
3. Eseguire le applicazioni con i permessi minimi necessari al suo funzionamento (*least privilege*)
4. Ridurre il codice che viene eseguito in un contesto privilegiato
5. Implementare il multifactor
6. Debugging
7. Eseguire i servizi con account non privilegiati
8. Testare gli errori di applicazioni e S.O.
9. Utilizzare la separazione dei privilegi (*separation of duties*)
10. Patchare e aggiornare il S.O.

Creare e mantenere l'accesso
-----

Eseguire applicazioni malevoli nei sistemi ha molti obiettivi tra i quali: accesso non autorizzato, cracking di password, screenshot delle schermate, installazione di backdoor.

#### Spyware
Gli spyware sono programmi *stealth* che registrano le attività di un utente senza che questo se ne accorga, le informazioni raccolte vengono inviate all'attaccante. Gli spyware nascondono i propri processi e file per non consentirne la rilevazione e la rimozione.

Tecniche di offuscamento di programmi malevoli
-----

#### Rootkit
I *rootkit* sono programmi che nascondono la propria presenza e le attività malevole dell'attaccante, rimpiazzano alcune *system call* e/o strumenti con la propria versione modificata. La struttura di un rootkit comprende backdoor, programmi per attacchi DDoS, packet sniffer, programmi per la rimozione di log, bot IRC.

#### Tipologie di Rootkit
* HYPERVISOR LEVEL ROOTKIT
* HARDWARE/FIRMWARE ROOTKIT
* KERNEL LEVEL ROOTKIT
* BOOT LOADER LEVEL ROOTKIT
* APPLICATION ROOTKIT
* LIBRARY LEVEL ROOTKIT

#### Come difendersi dai Rootkit
Reinstallare il S.O. o le applicazioni da una sorgente certificata dopo aver effettuato il backup dei dati critici. Effettuare un dump della memoria kernel per determinare la presenza di rootkit. Rinforzare le workstation/server contro gli attacchi. Installare network firewall e host-based firewall. Verificare l'integrità dei file di sistema regolarmente, utilizzando tecnologie crittograficamente resistenti.

#### NTFS Data Stream
Il NTFS Alternate Data Stream (ADS) è uno stream Windows nascosto che contiene metadati come attributi, conteggio parole, nome autore e accesso, data di modifica.
L'ADS permette ad un attaccante di iniettare codice malevolo nei file.

#### Steganografia
La steganografia è una tecnica di offuscamento, permette di nascondere messaggi all'interno di altri messaggi (all'apparenza normali) o a tipi di file diversi come video, audio e immagini. Permette di mantenere la confidenzialità del dato.
L'utilizzo più comune è tramite immagini nelle quali viene iniettato il messaggio segreto.

Tecniche di offuscamento delle evidenze di compromissione
-----

Una volta che un attaccante è riuscito ad ottenere un accesso amministrativo al sistema, esso cercherà di nascondere le proprie tracce per evitare di essere scoperto:

1. Disabilitare l'auditing
2. Ripulire i log
3. Manipolare i log

#### Coprire le tracce BASH
Bash memorizza la cronologia dei comandi eseguiti in un file chiamato *.bash_history*, un attaccante può eliminare o ripulire questo file con il comando `history -c` oppure `history -w`, per effettuare un'eliminazione più profonda si può ricorrere al comando `shred $HOME/.bash_history`.
