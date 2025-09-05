- Questo rielaborato comincia a partire dalle slide sul livello di trasporto, lezione 6
- Il rielaborato prima di queste slide è [[Reti di elaboratori - Fino a SMTP.pdf|qui]]

# Introduzione

## La rete

Una rete è composta da __nodi__, che si differenziano in:
- __Sistema terminali__ quali macchine degli utenti e server.
- __Dispositivi di interconnessione__ quali router, switch e modem.
Questi sono tutti collegati tramite __link__ (Collegamenti), che possono essere:
- Cablati, come in rame o in fibra ottica.
- Wireless, attraverso le onde elettromagnetiche o tramite satellite.

## Dispositivi di interconnessione

I dispositivi di interconnessione __rigenerano__ o __modificano__ il segnale che ricevono e si distinguono in:
- Router, un dispositivo che collega una rete ad altre reti.
- Switch (Commutatori), un dispositivo che collega più sistemi terminali a livello locale.
- Modem, un dispositivo che trasforma i dati digitali (bit) in dati analogici della linea telefonica e viceversa.

## Classificazione delle reti

| Scala     | Tipo                                  | Esempio        |
| --------- | ------------------------------------- | -------------- |
| Vicinanze | PAN (Personal Area Network)           | Bluetooth      |
| Edificio  | LAN (Local Area Network)              | WiFi, Ethernet |
| Città     | MAN (Metropolitan Area Network)       | Cavi, DSL      |
| Paese     | WAN (Wide Area Network)               | ISP            |
| Mondo     | Internet (network di tutti i network) | Internet       |
## Rete LAN

Una rete LAN è solitamente una rete __privata__ che collega i sistemi terminali di uno spazio specifico locale.

Quando un sistema terminale stabilisce un link con la rete LAN, gli viene assegnato un indirizzo IP, cioè un identificatore nella rete.

Ci sono due tipi di LAN:
- LAN con cavo condiviso (Broadcast).
- LAN a commutazione (con switch).

### LAN con cavo condiviso

Nella rete LAN con cavo condiviso, tutti i nodi sono collegati tramite cavo, e quando un nodo invia un pacchetto, questo viene ricevuto da __tutti__ gli altri nodi anche se solamente il destinatario effettivo lo elaborerà, mentre gli altri lo ignoreranno.

Si specifica che solamente un nodo alla volta può inviare pacchetti sulla rete.

### LAN a commutazione

Nella rete LAN a commutazione, tutti i sistemi terminali sono collegati a uno __switch__ che è in grado di:
- Ricevere i pacchetti inviati dai vari nodi.
- Riconoscere l'indirizzo di destinazione di ogni pacchetto.
- Inviare ogni pacchetto solo al suo destinatario.

Più nodi possono inviare pacchetti allo stesso tempo.

## Rete WAN

Una rete WAN interconnette dispositivi di connessione come modem, switch e router.

È gestita da un operatore di telecomunicazioni (ISP).

Ci sono due tipi di WAN:
- WAN punto-punto, è una rete che collega due reti tramite un link.
- WAN a commutazione, è una rete con più di due punti di terminazione.

## Rete a commutazione di circuito (Circuit-switched network)

Per questo tipo di rete viene stabilito un collegamento chiamato __circuito__, sulla quale avverrà l'intera comunicazione tra i $2$ dispositivi.

Le risorse necessarie al circuito vengono __riservate__ per tutta la durata della connessione.
Quindi questo tipo di rete garantisce una certa quantità di banda durante la comunicazione.

Per ottimizzare la gestione delle risorse si applicano metodi come il:
- __Frequency Division Multiplexing__, cioè il dividere la risorsa in modo tale che ogni dispositivo possa continuamente usare una certa quantità della risorsa.
- __Time Division Multiplexing__, cioè il suddividere la risorsa nel tempo, cosicchè ogni dispositivo possa usare l'intera risorsa per un periodo di tempo fissato.

## Rete a commutazione di pacchetto (Packet-switched network)

La comunicazione fra i $2$ nodi avviene trasmettendo blocchi di dati detti __pacchetti__.

Quindi non serve riservare risorse per mantenere la comunicazione.

I router invece adesso devono ricevere, memorizzare e inviare i pacchetti che gli arrivano.

Ogni pacchetto è indipendente dagli altri.

Durante la comunicazione tra $2$ nodi i pacchetti possono __non seguire__ un percorso specifico.

## Reti di accesso (Access network)

Sono le reti che collegano un nodo fino al primo __edge router__, cioè fino al primo router del __backbone__.

### Backbone Internet

È una rete composta esclusivamente di router e di link tra router, sulla quale si utilizza la commutazione a pacchetto.

## Struttura di Internet

Internet è strutturato in modo gerarchico:
- Al centro ci sono gli ISP di livello $1$, che operano su vasta scala.
- Gli ISP di livello $2$ usufruiscono della rete di livello $1$.
- Infine gli ISP di livello $3$ e quelli locali sono client dei ISP di livello $2$, e sono le reti più vicine ai sistemi terminali.

# Capacità e prestazioni delle reti

## Ampiezza di banda (Bandwidth)

È una caratteristica del canale trasmissivo la cui quantità rappresenta quanto il canale riesce a trasmettere.

Quindi maggiore è l'ampiezza di banda maggiore è la quantità di informazione che si riesce a trasmettere.

È misurata in $Hz$ (Hertz).

## Velocità di trasmissione (Bitrate)

Altro significato che la bandwidth assume è la quantità di bit che si riesce a trasmettere nell'unità di tempo.

La velocità di trasmissione (Bitrate), è quindi la quantità di bit al secondo che un link garantisce di trasmettere (Imettere nel canale).

Serve a fornire un'indicazione della capacità della rete di trasferire dati.

## Throughput

Il throughput indica quanto effettivamente la rete è in grado di inviare dati.

È la misura dell'effettiva velocità di un link ed è misurata in numero di bit al secondo.
Questa velocità, rispetto al bitrate, può variare nel tempo.

Il throughput "end to end", cioè dalla sorgente alla destinazione, è limitato dal link con il throughput più basso dell'intero percorso (Bottleneck).

## Ritardo dei pacchetti

I possibili ritardi sui pacchetti sono:
- Ritardo di elaborazione del nodo.
- Ritardo di accodamento.
- Ritardo di trasmissione.
- Ritardo di propagazione.

### Ritardo di elaborazione del nodo (Processing delay)

È il tempo (somma dei tre) impiegato per:
- Controllare l'integrità del pacchetto o degli errori sui bit.
- Determinare il canale di uscita, cioè a quale router successivo inviare il pacchetto. (Tabella di routing)
- Il pacchetto per transitare dalla porta di input a quello di output.

### Ritardo di accodamento (Queueing delay)

È il tempo in attesa nei buffer di input e di output.
Dipende dal livello di congestione del router.

### Ritardo di trasmissione (Transmission delay)

È il tempo richiesto per trasmettere tutti i bit del pacchetto sul link.

Se il primo bit del pacchetto viene trasmesso al tempo $t_{i}$ e l'ultimo bit del pacchetto viene messo in linea al tempo $t_{f}$, il ritardo di trasmissione del pacchetto è $t_{f}-t_{i}$.

Questo ritardo si calcola come:$$Ritardo\space di\space trasmissione=\frac{Lunghezza\space del\space pacchetto(bit)}{Bitrate\space del\space collegamento(bps)}$$

### Ritardo di propagazione (Propagation delay)

È il tempo che un bit impiega per propagarsi sul link, cioè per muoversi dal router mittente al destinatario.

Questo ritardo si calcola come:$$Ritardo\space di\space propagazione=\frac{Lunghezza\space del\space collegamento}{Velocità\space di\space propagazione}$$
La velocità di propagazione è la velocità con la quale viaggia un bit.

## Intensità di traffico

Più è alta l'intensità di traffico e più alto è il ritardo medio di accodamento.

L'intensità di traffico dipende:
- Dal tasso di arrivo dei pacchetti.
- Dalla loro lunghezza.
- Dal Bitrate.

Se l'intensità è:
- Circa nullo $\to$ Allora non c'è ritardo.
- Si avvicina a $1\to$ Allora esiste ritardo.
- Supera $1\to$ Allora ritardo infinito. (Cioè più lavoro in arrivo di quanto possa essere effettivamente svolto)

## Prodotto rate\*ritardo

Il prodotto rate\*ritardo rappresenta il massimo numero di bit che possono essere nel collegamento (allo stesso tempo).

Si calcola come:$$Prodotto\space rate\space ritardo=Bitrate\cdot RTT$$
Il Roundtrip time (RTT) è $2$ volte il ritardo di propagazione.

# Livello Applicazione

## Messaggi di richiesta HTTP

![|550](https://i.imgur.com/oLFx2Kc.png)
![|550](https://i.imgur.com/sqJZHL2.png)

### Header nella richiesta HTTP

- Host $\to$ Indica l'hostname richiesto e opzionale il numero di porta TCP del server
- Connection $\to$ Indica se si deve chiudere la connesione dopo aver ricevuto la risposta.
- User-agent $\to$ Indica il programma client utilizzato.
- Accept $\to$ Indica il formato dei contenuti che il client è in grado di accettare.
- Accept-charset $\to$ Indica la famiglia di caratteri che il client è in grado di gestire.
- Accept-encoding $\to$ Indica lo schema di codifica supportato dal client.
- Accept-language $\to$ Indica il linguaggio preferito dal client.
- Authorization $\to$ Indica le credenziali possedute dal client.
- Date $\to$ Indica la data e l'ora del messaggio.
- Upgrade $\to$ Specifica il protocollo di comunicazione preferito.
- Cookie $\to$ Comunica il cookie al server.
- If-Modified-Since $\to$ Invia il documento solo se è più recente della data specificata.

## Messaggio di risposta HTTP

![|550](https://i.imgur.com/EnAKjhA.png)
![|550](https://i.imgur.com/AF7scFv.png)

## Protocollo SMTP

I comandi sono:
```bash
# comincia il server con 220 hostname_suo
HELO hostname_mio
# risponde con 250 Hello hostname_mio, pleased to meet you
MAIL FROM: mail.address1
# risponde con 250 mail.address1 ...
RCPT TO: mail.address2
# risponde con 250 mail.address2 ...
DATA
# risponde con 354 Enter mail, end with "."
// Testo della mail
// Testo della mail
.
# risponde con 250 Message accepted for delivery
QUIT
# risponde con 221 hostname_suo
```

Il protocollo SMTP __non__ può essere usato dall'user agent del destinatario in quanto è un protocollo __push__, mentre deve invece eseguire un'operazione __pull__.

## Protocollo POP3

Non si può rileggere i messaggi se cambia client.
È un protocollo senza stato tra le varie sessioni.
Non fornisce all'utente procedure per creare cartelle remote e assegnare loro messaggi.
Dopo che l'utente recupera le mail e chiude la connessione, il server __cancella__ i messaggi marcati per la rimozione.

## Protocollo IMAP

Mantiene tutti i messaggi nel server.
Consente all'utente di organizzare i messaggi in cartelle.
È un protocollo che conserva lo stato dell'utente tra le varie sessioni:
- I nomi delle cartelle.
- L'associazione tra identificatori dei messaggi e nomi delle cartelle.

## Protocollo FTP

È un protocollo utilizzato per il trasferimento di file da un host remoto o a un host remoto.

Il protocollo FTP apre __due__ connessioni TCP:
- Sulla porta $21$ apre una connessione di controllo TCP.
- Sulla porta $20$ apre una connessione dati TCP.

Quando l'user fornisce il hostname del host remoto, il processo client FTP stabilisce una connessione TCP sulla porta 21 con il processo server FTP.

Una volta stabilita la connessione, il client fornisce dati per l'identificazione, e queste vengono inviate sulla connessione di controllo FTP.

Dopo ogni trasferimento di un file, il server __chiude__ la connessione dati, ma __non__ quella di controllo.

Quindi la connessione di controllo è __fuori banda__ (Out of band) in quanto non è la connessione sulla quale viaggiano anche i dati.

Il server FTP __mantiene__ lo __stato__:
- Mantiene la directory corrente.
- Mantiene l'autenticazione precedente.
(dato che la connessione di controllo rimane attiva, non ha senso richiedere di nuovo identificativo utente e password ogni volta...)

I comandi sono:
```bash
ftp Hostname
ftp > USER username
ftp > PASS password
ftp > LIST # elenca i file della directory corrente
ftp > RETR filename o path # è un get
ftp > STOR filename o path # è un put
```


# Livello Trasporto
## Connessione a livello trasporto

I protocolli di trasporto forniscono la __comunicazione__ tra __processi__ delle applicazioni di host differenti.

I protocolli di trasporto vengono eseguiti nei __sistemi terminali__, dove essi svolgono le operazioni di __incapsulamento__ dei messaggi in __segmenti__ per passarli al livello di rete, oppure svolgono le operazioni di __decapsulamento__ dei segmenti in __messaggi__ per passarli al livello di applicazione.
(il protocollo TCP __segmenta__ i messaggi $\to$ segmenti)

## Relazione tra i 3 livelli dello stack protocollare TCP/IP

Livello di __applicazione__ serve per la comunicazione tra applicazioni dei host (e.g. web browser)
Livello di __trasporto__ serve per la comunicazione tra processi
Livello di __rete__ serve per la comunicazione tra host

## Indirizzamento dei processi

Quando si deve stabilire una comunicazione tra due processi, è necessario identificare gli __host__ (client e server) dei due processi, e i __processi__ stessi, in quanto all'interno di un host si possono avere diversi processi attivi.

Per individuarli si usa:
- L'__indirizzo IP__ per gli host
- Il __numero di porta__ per i processi

Quindi l'indirizzamento del livello di trasporto è dato dal numero di porta mentre quello del livello di rete è dato dall'indirizzo IP

## Indirizzo Socket

Quando un processo di un applicazione del client genera un messaggio, a questo viene associato un numero di porta che lo identifica tra i vari processi del client.
Dopodiché, nel passaggio dal livello trasporto al livello di rete, al pacchetto viene associato l'indirizzo IP del client.
Questa coppia indirizzo IP e numero di porta costituiscono quello che è l'__indirizzo socket__.

## Incapsulamento/Decapsulamento (Livello trasporto)

Una volta passato al livello trasporto, il messaggio proveniente dal livello applicazione viene __incapsulato__ insieme a un __header__ (Intestazione) in un pacchetto chiamato __segmento__ (TCP) o __datagramma utente__ (UDP).

All'interno dell'header è presente sia il numero di porta del mittente che del destinatario.

Quando il segmento arriverà al destinatario, verrà __decapsulato__ al livello trasporto per poi essere mandato al processo del livello applicazione, identificato tramite il numero di porta ottenuto durante il decapsulamento.

## Multiplexing/Demultiplexing (Livello trasporto)

Il livello trasporto deve poter ricevere __messaggi__ da __diversi__ processi allo stesso tempo, che dovrà gestire uno alla volta, dove per ognuno deve incapsularlo e mandarlo al livello sottostante.

Alla ricezione, il livello trasporto esegue il demultiplexing, cioè andrà a consegnare il pacchetto al processo corretto in base al numero di porta che è presente nell'__header__.

## Header (Intestazione) del livello trasporto

![|250](https://i.imgur.com/kmGu5BG.png)

Il pacchetto UDP/TCP è composto dal messaggio del processo di livello applicazione insieme a un header creato dal livello trasporto che viene incapsulato insieme al messaggio.
Sulla prima riga del header troviamo i numeri di porta dei host mittente e destinatario, entrambi formati da $16\space bit$.
Sulla seconda riga si trovano altri campi riguardanti altre informazioni come la dimensione in bit dei numeri di sequenza.

### Numeri di porta riservati

I numeri di porta dal 0 al 1024 sono __riservati__ per processi noti. (e.g. HTTP ha porta $80$)

## Gestione del passaggio dei messaggi dal livello applicazione al trasporto

Viene utilizzato un API di comunicazione, la __socket API__, che è l'interfaccia che c'è tra il livello applicazione e il livello trasporto.
Permette di interagire con il livello trasporto e di passare pacchetti ad esso.

## Comunicazione tra processi

La comunicazione tra processi avviene mediante __socket__.
Cioè quando un processo comunica con un altro processo, in realtà si sta comunicando al socket del processo.
## (Indirizzo) Socket

È una struttura dati composta dalla coppia:
- __Indirizzo IP
- __Numero di porta__

## Individuare i socket lato client

Il client ha bisogno di un socket address __locale__ e un socket address __remoto__ per sapere a chi inviare messaggi.

Il socket address locale viene fornito dal __sistema operativo__, dato che esso conosce sia l'indirizzo IP della macchina, sia i vari processi che stanno venendo eseguiti, e quindi i loro numeri di porta.
- Quindi il socket address locale presenta un numero di porta detto __effimero__, ovvero temporaneo, che dura per la durata della comunicazione. E tale numero di porta non sarà usato da altri processi.

Il socket address remoto ha il numero di porta noto in base all'applicazione alla quale si vuole comunicare (e.g. HTTP ha porta $80$), mentre l'indirizzo IP viene fornito dal __DNS__.
- Oppure entrambi sono noti perché dati dal programmatore quando si vuole verificare il funzionamento di un'applicazione.

## Individuare i socket lato server

Il server ha bisogno di un socket address __locale__ e un socket address __remoto__ per sapere a chi rispondere i messaggi in arrivo.

Il socket address locale viene fornito dal __sistema operativo__, dato che esso conosce l'indirizzo IP della macchina server. Mentre il numero di porta è noto al server perché viene assegnato dal progettista durante la creazione del server. (e.g. Un server HTTP è sempre in ascolto sulla porta $80$)

Il socket address remoto è il socket address locale di un client che si connette al server.
- Quindi l'indirizzo IP e il numero di porta del socket address remoto sono conosciuti dal server quando al livello di rete e al livello trasporto si decapsulano gli header rispettivi dal pacchetto arrivato che comprendono queste informazioni.

## Servizi dei protocolli di trasporto

Il __servizio di TCP__ (protocollo affidabile):
- È __orientato alla connessione__, cioè viene stabilita una connessione accordata tramite uno scambio di messaggi iniziale tra il client e il server. Tale connessione è dedicata.
- Il __trasporto__ dei messaggi fra processi mittente e destinatario è __affidabile__, ovvero senza errori, ciò che viene inviato arriverà alla destinazione senza perdite di dati e nell'ordine con la quale sono stati inviati.
- È implementato nel servizio di TCP il __controllo di flusso__, cioè viene sorvegliato la quantità di informazioni che si invia al destinatario, in modo tale da non sovraccaricarlo. Quando ciò accade, il controllo di flusso provvederà a rallentrare la frequenza di invio di informazioni al destinatario.
- È implementato all'interno del servizio di TCP il __controllo della congestione__, che si attiva per limitare il processo che invia messaggi quando nota che la __rete__ è sovraccaricata a causa di un rallentamento o blocco di un __nodo intermedio__ (Router).
ma non offre:
- __Servizi di temporizzazione__, cioè non garantisce che un pacchetto sia trasmesso in un certo tempo.
- __Garanzie sull'ampiezza di banda__, cioè non garantisce che un client possa usufruire di una certa ampiezza di banda.
- __Sicurezza__, serve avere protocolli aggiuntivi (TCP all'inizio non presentava servizi per la sicurezza dei pacchetti).

Il __servizio di UDP__ (protocollo non affidabile):

- È __senza connessione__, cioè non è richiesto alcun setup tramite messaggi tra il client e il server.
- Il __trasporto__ dei messaggi fra processi mittente e destinatario è __inaffidabile__, cioè non è sicuro che i pacchetti inviati arrivino, e se arrivano possono essere non in ordine di invio.
- __Controllo degli errori sul singolo datagramma__, grazie al __checksum__.
e non offre:
- __Setup della connessione__ (Non è orientato alla connessione).
- __Affidabilità__ (Non è affidabile).
- __Controllo di flusso__.
- __Controllo della congestione__.
- __Servizi di temporizzazione__.
- __Garanzie sull'ampiezza di banda minima__.
- __Sicurezza__.
ma è:
- __Veloce__

![|550](https://i.imgur.com/PZP7s8b.png)

## Protocollo UDP (User Datagram Protocol) (Livello Trasporto)

Il protocollo di trasporto UDP è inaffidabile ed è privo di connessione.
Fornisce comunque i servizi di:
- [[Reti di elaboratori#Comunicazione tra processi|Comunicazione tra processi utilizzando i socket]].
- [[Reti di elaboratori#Multiplexing/Demultiplexing (Livello trasporto)|Multiplexing/Demultiplexing dei pacchetti]].
- [[Reti di elaboratori#Incapsulamento/Decapsulamento (Livello trasporto)|Incapsulamento e decapsulamento]].

### Comunicazione in UDP

Il mittente invia pacchetti in modo continuo senza pensare alla congestione da parte del destinatario in quanto non è presente un controllo di flusso o di congestione.

Il mittente deve __dividere__ i suoi messaggi in __porzioni__ di dimensioni che possono essere gestiti dalla rete.

Ogni pacchetto è indipendente dagli altri, cioè che l'ordine in cui sono stati inviati non necessariamente è lo stesso di quello di arrivo.

### Struttura del datagramma UDP

Il messaggio del processo per poter essere inserito all'interno di un datagramma deve avere dimensione __inferiore__ a $65507\space byte$, in quanto dei $65535$, $8\space byte$ sono assegnati all'header (Intestazione) UDP e $20\space byte$ all'header IP.

Il datagramma UDP presenta $4$ campi da $2\space byte$ come __intestazione__:
- $2\space byte$ per il __numero di porta del mittente__.
- $2\space byte$ per il __numero di porta del destinatario__.
- $2\space byte$ per indicare la __lunghezza in byte__ del segmento UDP, inclusa l'intestazione.
- $2\space byte$ per il __checksum__, una stringa che serve per controllare se il pacchetto arrivato è corrotto (bit cambiati).

### Checksum UDP

Per poter utilizzare il checksum il mittente:
1) Divide il messaggio in __"parole"__ da $16\space bit$.
2) Il valore del checksum viene inizialmente impostato a zero.
3) Tutte le parole del messaggio, incluso il checksum, venogno sommate usando l'addizione complemento ad uno.
4) Viene fatto il complemento ad uno della somma e il risultato è il checksum.
5) Il checksum viene inviato assieme ai dati.
mentre il destinatario:
6) Riceve il messaggio.
7) Divide il messaggio in parole da $16\space bit$.
8) Tutte le parole vengono sommate usando l'addizione complemento ad uno.
9) Viene fatto il complemento ad uno della somma e il risultato diventa il nuovo checksum.
10) Se il valore del checksum è 0 allora il messaggio viene accettato altrimenti viene scartato.

### DNS usa UDP

Il protocollo DNS del livello applicazione utilizza servizi dati dal protocollo UDP del livello trasporto.
Questo perché DNS è un protocollo __molto semplice__ basato su un interazione __molto veloce__ di richiesta/risposta. Non richiede l'invio di __grandi file__, non deve fare setup tra host, e quindi risulta molto efficace usare il protocollo UDP.

## Protocollo TCP (Livello Trasporto)

Il protocollo di trasporto TCP invia pacchetti in un flusso di byte.
Il protocollo di trasporto TCP è affidabile ed è orientato alla connessione.
Fornisce servizi di:
- [[Reti di elaboratori#Comunicazione tra processi|Comunicazione tra processi utilizzando i socket]].
- [[Reti di elaboratori#Multiplexing/Demultiplexing (Livello trasporto)|Multiplexing/Demultiplexing dei pacchetti]].
- [[Reti di elaboratori#Incapsulamento/Decapsulamento (Livello trasporto)|Incapsulamento e decapsulamento]].
- [[Reti di elaboratori#Servizi dei protocolli di trasporto|Controllo di flusso]].
- [[Reti di elaboratori#Servizi dei protocolli di trasporto|Controllo degli errori]].
- [[Reti di elaboratori#Servizi dei protocolli di trasporto|Controllo della congestione]].

### Demultiplexing orientato alla connessione (Protocollo TCP)

Il demultiplexing nel protocollo TCP è basato su un socket TCP che non è più una coppia:
- Indirizzo IP + Numero di porta.
È costituito invece da __due__ coppie:
- Indirizzo IP del mittente + Numero di porta del mittente
- Indirizzo IP del destinatario + Numero di porta del destinatario

L'host che riceve il segmento usa questi __quattro parametri__ per inviare il segmento risposta alla socket appropriata.

Ogni richiesta di connessione da parte del client su una porta del server porta all'inizializzazione di un nuovo __thread__ per gestire in modo più veloce tale richiesta, così ogni connessione avrà sul server un suo "processo" distinto che la gestisce.

I server web hanno socket __differenti__ per ogni connessione client:
- con HTTP __non-persistente__ si avrà una socket differente anche per ogni richiesta dallo __stesso client__.

### Servizio orientato alla connessione (Protocollo TCP)

Due host, prima di poter inviare e ricevere messaggi, devono __stabilire una connessione logica__ (Astratta, non fisica), cioè si deve all'inizio richiedere l'__apertura__ della connessione, e alla fine dello scambio di dati, si deve richiedere la __chiusura__ della connessione.

### Procedimento per stabilire una connessione TCP

Partendo dallo stato "closed", ovvero quando la connessione è inesistente:
1) Il mittente manda una richiesta al destinatario.
2) Il destinatario riceve la richiesta e restituisce al mittente un __Ack__ (nowledgement) per accettare la richiesta.
3) Il mittente ricevuto l'Ack del destinatario, gli manda un Ack per rispondere all'Ack ricevuto.
A questo punto la connessione si può definire stabilita, e si può cominciare a spedire pacchetti.
Tale procedimento si chiama __"3 way handshake"__.

Quando si deve chiudere la connessione sarà eseguito un procedimento analogo a quello di apertura.

### Controllo di flusso del TCP (Introduzione)

Durante il trasferimento dei dati fra due host, un produttore e un consumatore, ci deve essere un controllo che __gestisce la velocità__ con la quale si __immettono__ questi dati.
- Perché se la velocità di produzione è __maggiore__ della velocità di consumo, allora il consumatore potrebbe essere __sovraccaricato__ e costretto a eliminare alcuni di questi dati.
- Perché se la velocità di produzione è __minore__ della velocità di consumo, allora il consumatore rimane __in attesa__, riducendo l'__efficienza__ del sistema.

Il controllo di flusso è legato al problema di un possibile sovraccarico del consumatore.

Una possibile soluzione è quella di usare dei __buffer__, ovvero delle locazioni di memoria che possono contenere pacchetti.
È necessario da parte del destinatario inviare dei __segnali__ per comunicare al mittente la quantità di spazio rimanente nel suo buffer, così in modo da segnalare al livello trasporto del mittente di __sospendere momentaneamente__ l'invio di messaggi se si __satura__ il buffer, o per far __riprendere__ l'invio una volta liberato spazio nel buffer.

Il controllo di flusso quindi modifica in continuazione la __quantità__ di pacchetti che si possono spedire al destinatario.

### Controllo degli errori del TCP (Introduzione)

Per errore non si intede la corruzione di un pacchetto ma bensì la errata sequenza di arrivo dei pacchetti.

Poiché il livello di rete è inaffidabile, a causa di rallentamenti o perdite di dati, il livello trasporto deve gestire questi problemi, attraverso l'implementazione di un meccanismo di numerazione dei pacchetti.

La numerazione dei pacchetti avviene tramite l'inserimento di un campo all'interno dell'header, che è il __numero di sequenza__.
Tale numero è sequenziale, ed è limitato dalla quantità di bit assegnata nell'intestazione, quindi una volta arrivata alla dimensione massima, ripartirà ciclicamente da zero.
Il massimo possibile è $2^{16}$. (credo)

Il numero di sequenza è utile al destinatario per capire:
- Se la sequenza dei pacchetti in arrivo è corretta.
- Se mancano pacchetti.
- Se ci sono pacchetti duplicati.
ma non permette di capire se un pacchetto è __andato perso__.

Quindi serve un ulteriore valore, il __numero di riscontro__ (Ack), che permette di notificare al mittente la corretta ricezione di un pacchetto.

### Integrazione del controllo di flusso e degli errori

È possibile combinare i due controlli mediante l'uso di un __buffer numerato__ presso il mittente e il destinatario.

Il mittente:
- Quando prepara un nuovo pacchetto usa come numero di sequenza il numero $x$ della prima locazione libera nel buffer.
- Quando invia il pacchetto ne memorizza una copia nella locazione $x$.
- Quando riceve un Ack di un pacchetto libera la posizione di memoria che era occupata da quel pacchetto.
mentre il destinatario:
- Quando riceve un pacchetto con numero di sequenza $y$, lo memorizza nella locazione $y$ fino a quando il livello applicazione non sarà pronto a riceverlo.
- Quando il pacchetto $y$ passa al livello applicazione invia un Ack del pacchetto $y$ al mittente.

### Controllo della congestione

Nella commutazione a pacchetto, la congestione avviene se il numero di pacchetti inviati in rete è superiore al numero di pacchetti che la rete può evadere.

### Stop-and-wait (Meccanismo trasferimento dati affidabile TCP)

È un __meccanismo__ per il controllo del flusso e degli errori.

In questo meccanismo l'host mittente e l'host destinatario usano entrambi una __finestra scorrevole di dimensione__ $1$, cioè possono contenere un solo pacchetto alla volta.
(Quando il pacchetto viene inviato, il mittente lo memorizza nella sua finestra finché non gli arriva l'Ack di quel pacchetto, questo per ricordarsi cosa ha spedito e cosa deve rispedire se non gli arriva l'Ack)

Il mittente quindi invia un pacchetto e aspetta il ritorno dell'Ack prima di spedire quello successivo.
Quando il pacchetto arriva al destinatario, viene calcolato il __checksum__:
- Se il pacchetto è __corretto__, allora viene inviato l'Ack al mittente.
- Se il pacchetto è __corrotto__, allora il pacchetto viene __scartato__ senza informare il mittente.
Quindi il mittente per capire se un pacchetto da lui inviato non è stato accettato perché corrotto, fa uso di un __timer__ in quanto non può aspettare all'infinito.

Il controllo di flusso è implementato implicitamente in quanto non si può spedire più di un pacchetto alla volta.

Il controllo degli errori è implementato mediante il __numero di sequenza__, gli __Ack__ e il __timer__.

Per convenzione il numero di riscontro (Ack) indica il numero di sequenza del prossimo pacchetto atteso dal destinatario.
- Cioè se il destinatario ha ricevuto correttamente il pacchetto $x$, allora invia un Ack con valore $x+1$, che significa che sta aspettando il pacchetto con numero di sequenza $x+1$.

L'efficienza del meccanismo Stop-and-wait è molto basso.

### Meccanismi di trasferimento dati affidabile con pipeline TCP

Esistono meccanismi molto più efficienti del Stop-and-wait, grazie all'uso di __pipelines__, dove il mittente invia più pacchetti al destinatario, anche quando non gli è arrivato indietro l'Ack del primo pacchetto.

L'intervallo dei numeri di sequenza allora deve essere __incrementato__.

### Go back N (Meccanismo trasferimento dati affidabile con pipeline TCP)

È un __meccanismo__ per il controllo del flusso e degli errori nel protocollo TCP.

Rispetto al Stop-and-wait, il Go back N presenta una finestra di __invio__ di __multiple posizioni__, ma mantiene la __stessa__ dimensione della finestra di __ricezione__ del Stop-and-wait, ovvero $1$.

I numeri di sequenza sono calcolati sempre in modulo $2^m$ dove $m$ è la dimensione nell'intestazione del campo "numero di sequenza" in bit.
- Tipo se posso usare $3\space bit$ per il campo "numero di sequenza" allora la dimensione massima della finestra di invio sarà di $2^3-1=7$ pacchetti.

Il funzionamento del meccanismo è che quando il mittente invia più pacchetti, nella sua finestra di invio (il suo buffer), contiene __due puntatori__:
- $S_{f} \to$ che segna il più vecchio pacchetto inviato non ancora riscontrato (non Ackkato). (Send First)
- $S_{n} \to$ che segna il prossimo pacchetto da inviare (può inviare fino alla rimanente dimensione della finestra di invio). (Send Next)

Quando il destinatario riceve correttamente un pacchetto, manda al mittente l'Ack che indica la corretta ricezione del pacchetto, e che sta aspettando il successivo:
- Destinatario manda $AckNo=7$, allora i pacchetti fino al $6$ sono stati ricevuti correttamente e il destinatario sta attendendo il $7$.
- Mittente manda $5$ pacchetti, con numero di sequenza da $0$ a $4$, ma il pacchetto $5$ è stato perso, allora il destinatario manda indietro $4$ Ack, dal $1$ fino al $5$, invece che fino al $6$, in modo da far capire al mittente che il quinto pacchetto inviato è stato perso, e che deve rispedirlo, invece di mandare i pacchetti succesivi al $5$.
- Quando un Ack $x$ e un Ack $x+1$ vengono mandati dal destinatario, e l'Ack $x$ viene perso, quindi il mittente riceve solamente l'Ack $x+1$, questo Ack viene considerato __cumulativo__, nel senso che il mittente segnerà come riscontrato anche il pacchetto $x$. 

Il destinatario però dato che possiede una finestra di ricezione di dimensione $1$, è sempre in attesa di uno __specifico__ pacchetto, e quindi qualsiasi pacchetto arrivato __fuori sequenza__ viene scartato.
Quindi se l'insieme di pacchetti in arrivo non ha "buchi" allora li riscontra tutti e invia Ack per quello successivo, ma se manca anche un solo pacchetto, allora tutti quelli arrivati successivamente li scarterà.

Il mittente mantiene un __timer__ per il __più vecchio__ pacchetto __non__ riscontrato.
E allo scadere del timer si va a rispedire __tutti__ i pacchetti in attesa di riscontro.

La __dimensione__ della finestra di invio deve essere __minore__ di $2^m$ dove $m$ è la dimensione nell'intestazione del campo "numero di sequenza" in bit.
Quindi la finestra di invio ha dimensione $2^{m}-1$.

### Selective repeat (Meccanismo trasferimento dati affidabile con pipeline TCP)

È un __meccanismo__ per il controllo del flusso e degli errori nel protocollo TCP.

Rispetto al Go Back N, nel Selective repeat:
- Il mittente ritrasmette __soltanto__ i pacchetti per i quali non ha ricevuto un Ack.
- Il destinatario prevede una finestra di ricezione di dimensione __uguale__ a quella di invio del mittente.

Il destinatario invia __Ack specifici__ per tutti i pacchetti ricevuti correttamente, sia per quelli in ordine, sia per quelli fuori sequenza.
Quindi il destinatario memorizza anche i pacchetti arrivati fuori sequenza ma comunque all'interno della finestra di ricezione.

Il __timer__ è presente, ma a questo punto non può essere legato al primo pacchetto inviato senza riscontro.
Nel Selective repeat esiste un timer __per ogni__ pacchetto in attesa di riscontro, e quando scade un timer, il mittente provvede a rinviare __solo__ il pacchetto relativo a tale timer.

Il riscontro è __individuale__ ed è associato al singolo pacchetto, cioè il numero di riscontro indica il numero di sequenza di un pacchetto ricevuto correttamente e __non__ il prossimo pacchetto che il destinatario attende.

Una volta riscontrata tutta la finestra, la si scorre.

La __dimensione__ delle finestre di invio e di ricezione deve essere di $2^{m-1}$ dove $m$ è la dimensione nell'intestazione del campo "numero di sequenza" in bit.

#### Vantaggi del meccanismo

Permette di rispedire meno pacchetti rispetto al Go back N

#### Svantaggi del meccanismo

È costoso a livello di computazione all'interno di ogni nodo il dover mantenere un timer per ogni pacchetto spedito.
Serve assegnare molto spazio per le finestre.

### Piggybacking

Il protocollo TCP utilizza un meccanismo __bidirezionale__, cioè quando un pacchetto trasporta dati da un host $A$ a un host $B$, può trasportare anche i riscontri relativi ai pacchetti ricevuti da $B$ e viceversa.

### Riassunto delle funzionalità dei meccanismi di trasferimento dati affidabile

La __checksum__ permette di gestire gli errori a livello di bit.
Gli __Ack__, il __numero di sequenza__ e il __timeout__ permettono di gestire gli errori a livello di pacchetto $\to$ pacchetto perso, Ack perso, pacchetto corrotto (non in ordine).
Le __finestre scorrevoli__ e il __pipelining__ permettono di migliorare le prestazioni della rete.

### Struttura del segmento TCP

Il messaggio del processo viene incapsulato insieme all'intestazione del segmento TCP.

Questa intestazione può avere dimensione variabile da $20\space bit$ fino a $60\space bit$, e contiene:
- Sulla prima riga:
	- $16\space bit$ per il __numero di porta del mittente__.
	- $16\space bit$ per il __numero di porta del destinatario__.
- Sulla seconda riga:
	- $32\space bit$ per il __numero di sequenza__, tale numero è il numero del __primo byte__ di dati contenuto nel segmento.
	     (e.g. Dati segmenti da $500\space byte$, il primo segmento ha numero di sequenza $1$, mentre il secondo invece avrà numero di sequenza $501$)
- Sulla terza riga:
	- $32\space bit$ per il __numero di riscontro (Ack)__, che indica il numero di sequenza del __prossimo byte atteso__ dal destinatario.
	     (e.g. Se il destinatario riceve un segmento di $500\space byte$ con numero di sequenza pari a $1001$, allora manderà un Ack di $1501$) 
- Sulla quarta riga:
	- $4\space bit$ per indicare la __lunghezza del header__, in quanto è __variabile__ la sua dimensione, e quindi è necessario capire quando inizia la parte dei dati del segmento.
	- $6\space bit$ __riservati__.
	- $6\space bit$ per i __flag__, $1\space bit$ per flag, descritti [[Reti di elaboratori#Flags del header del segmento TCP|sotto]].
	- $16\space bit$ per indicare la __dimensione della finestra__, che serve per il controllo di flusso. ([[Reti di elaboratori#Controllo di flusso del TCP (Effettivamente usato)|Dettagli qui]])
- Sulla quinta riga:
	- $16\space bit$ per la __checksum__.
	- $16\space bit$ per un __puntatore urgente__.
- Sulla sesta riga:
	- fino a $40\space byte$ per opzioni e padding (riempimento).

![|700](https://i.imgur.com/cHU86ju.png)

#### Flags del header del segmento TCP

Sono $6$ indicatori che se impostati a $1$ hanno significati precisi riguardo i dati e riguardo la connessione TCP.

I flag ACK, SYN, RST e FIN sono utilizzati per gestire la connessione TCP, cioè nei pacchetti di controllo che servono all'inizio e alla fine, quando viene stabilita e chiusa la connessione, vengono usati questi flag:
- ACK a $1$ significa che il segmento è anche un Acknowledgement.
- SYN a $1$ significa che il segmento è un segmento di sincronizzazione.
- RST a $1$ significa che si deve azzerare la connessione.
- FIN a $1$ significa che il segmento va a chiudere la connessione.

I flag URG e PSH riguardano i dati:
- URG a $1$ significa che si deve controllare il valore del campo del puntatore urgente, tale puntatore punta a dove finiscono i dati urgenti e quindi a dove iniziano quelli normali. I dati urgenti vengono vengono inseriti all'inizio del segmento. (e.g. quando si vuole interrompere un data transfer)
- PSH a $1$ significa che i dati del segmento devono essere passati subito al livello applicazione appena arrivano.

![|500](https://i.imgur.com/0UTpOtt.png)

### Apertura della connessione TCP (3 way handshake)

Per eseguire l'apertura di una connessione TCP tra due host è necessario che si __mandino $3$ pacchetti__.

Quindi se un client vuole aprire una connessione con un server:
- Il client manderà una richiesta di apertura della connessione al server.
- Questa richiesta __è un segmento TCP__ con il flag __SYN__ impostato a $1$ (tutti gli altri a $0$).
- All'interno di questo segmento __non ci sono dati__.
- Il segmento presenta un numero di sequenza $x$ __random__ scelto dal client, che diventerà quello __iniziale__ (Random ISN / Random Initial Sequence Number)

Quando il server riceve la richiesta dal client:
- Manda un Ack, ovvero un segmento con il flag __ACK__ impostato a $1$, e si aspetta di ricevere come prossimo segmento dal client un segmento con numero di sequenza pari a $x+1$.
- Il segmento in risposta alla richiesta è anch'essa una richiesta di apertura della connessione da parte del server con il client, e contiene quindi un numero di sequenza $y$ scelto dal server, perciò tale segmento avrà anche il flag SYN impostato a $1$.

Quando il client riceve il segmento di risposta (e richiesta) del server:
- Manda un Ack per confermare la richiesta del server e per informare il server che si aspetta di ricevere come prossimo segmento dal server un segmento con numero di sequenza pari a $y+1$.

Soltanto quando è arrivato l'__ultimo__ di questi $3$ pacchetti si può dire che la connessione è __aperta__.

### Chiusura della connessione

Ciascuna delle due parti coinvolta nello scambio di dati può richiedere la chiusura della connessione. (Solitamente è una richiesta dal client)

È un procedimento molto simile al procedimento per l'apertura.
Per eseguire la chiusura di una connessione TCP tra due host è necessario che si __mandino $3$ pacchetti__.

Quando un client vuole chiudere la connessione con un server:
- Manda un segmento con il flag FIN impostati a $1$. (Anche il flag ACK è impostato a $1$)

Quando il server riceve la richiesta di chiusura dal client:
- Manda un segmento con i flag ACK e FIN impostati a $1$.
- Il valore Ack del segmento inviato sarà il valore Ack del segmento precedente __aumentato__ di $1$.

Quando il client riceve il segmento di risposta del server:
- Manda un segmento con il flag ACK impostato a $1$ per indicare che ha ricevuto correttamente la conferma da parte del server della richiesta di chiusura.
- Il valore Ack del segmento inviato sarà il valore Ack del segmento precedente __aumentato__ di $1$.

Quando il server riceve quest'ultimo segmento allora si può dire che la connessione è stata __chiusa__.

### Controllo degli errori del TCP (Effettivamente usato)

Nel protocollo TCP, il controllo degli errori viene implementato attraverso un meccanismo che presenta elementi sia dal [[Reti di elaboratori#Go back N (Meccanismo trasferimento dati affidabile con pipeline TCP)|Go back N]] che dal [[Reti di elaboratori#Selective repeat (Meccanismo trasferimento dati affidabile con pipeline TCP)|Selective repeat]].

Il meccanismo usato dal TCP usa:
- Numero di sequenza, che è il numero del primo byte del segmento.
- Ack, che è il numero di sequenza del prossimo byte atteso dall'altro host e può essere cumulativo.
- Checksum.
- Timer di ritrasmissione associato al più vecchio pacchetto non riscontrato.
- Ritrasmissione, ma solo del segmento all'inizio del buffer (coda).

In particolare usa gli __Ack posticipati__:
- Quando arriva un segmento in modo normale (non ritrasmesso) e tale segmento è effettivamente il segmento con il numero di sequenza atteso, allora faccio partire un timer di $500\space ms$ durante la quale non invio subito l'Ack, ma aspetto il segmento subito dopo.
	- Se il segmento successivo arriva entro il timer $\to$ Allora invio un __Ack cumulativo__ per riscontrarli entrambi.
	- Se il segmento successivo non arriva entro il timer $\to$ Allora invio un __Ack posticipato__ per riscontrare solamente il segmento arrivato.

Inoltre:
- Se arriva un segmento __non ordinato__ con numero di sequenza __superiore__ a quello atteso, si ha un __buco__ $\to$ Allora si invia __immediatamente__ un Ack __duplicato__, dove si indica il numero di sequenza del prossimo byte atteso (Ritrasmissione rapida).
- Se arriva un segmento __mancante__ (leggi sopra), ovvero che serve per riempire un __buco__ $\to$ Allora si invia __immediatamente__ un Ack __cumulativo__.
- Se arriva una segmento __duplicato__ $\to$ Allora si invia __immediatamente__ un Ack con il numero di sequenza del prossimo byte atteso.

Quando un segmento viene inviato, ne viene memorizzata una sua copia in una coda in attesa di essere riscontrato, tale coda si chiama __finestra di invio__.

La __ritrasmissione__ avviene quando:
- Scade il timer, allora viene ritrasmesso il __primo__ segmento all'inizio della coda, e viene riavviato il timer.
- Vengono ricevuti $3$ Ack duplicati, allora si effettua la ritrasmissione veloce del primo segmento con numero di sequenza pari a quello dei $3$ Ack (senza che si attenda il timer).

È possibile che un Ack di uno o multipli segmenti venga perso, ma che non comporti ritrasmissioni in quanto l'Ack è cumulativo:
- Cumulativo nel senso che se il mittente dei segmenti non ha ancora riscontrato i segmenti $x$ e $x+1$ perché gli Ack di $x$ e $x+1$ sono stati persi, ma è arrivato un Ack di $x+2$, allora dato che l'Ack è cumulativo, il mittente potrà riscontrare tutti e $3$ i segmenti, ovvero $x$,$x+1$ e $x+2$.


### Controllo di flusso del TCP (Effettivamente usato)

L'obiettivo del controllo di flusso è il bilanciamento tra la velocità di invio con quella di ricezione.

Il destinatario invia dei __feedback espliciti__ al mittente:
- Comunica al mittente lo spazio disponibile attraverso l'uso del valore di __receive window__ (RcvWindow, RWND) presente come campo nell'__header__ dei segmenti TCP.

In base al valore del campo di RcvWindow inviato dal destinatario al mittente, la finestra di invio del mittente può aumentare o ridurre.

Si ricorda che la finestra di invio contiene due "puntatori":
- __Sf__, che sta per "Send First", ovvero il primo segmento in attesa di essere riscontrato.
- __Sn__, che sta per "Send Next", ovvero il prossimo segmento da inviare.
Quando il primo byte di un blocco di byte all'interno della finestra viene riscontrato, si rimuovono i byte per spostare la finestra in modo da avere un nuovo posto libero nel buffer.

Quindi la finestra (Buffer) di invio ha dimensione variabile in base all'ultimo Ack e all'ultimo valore di RWND ricevuto.

### Controllo della congestione

La congestione __non__ riguarda i host agli estremi ma riguarda invece i __nodi intermedi__.

Quando è presente la congestione si presentano dei sintomi che ci suggerisce la sua presenza:
- Pacchetti smarriti, in quanto rifiutati dai nodi intermedi quali __router__.
- Lunghi ritardi, in quanto la coda nei buffer si sta riempiendo.

La congestione è un problema che riguarda IP ma viene gestito da TCP.

Il controllo della congestione quindi viene effettuato in modo __end-to-end__, cioè la rete non fornisce supporto esplicito, e la congestione viene dedotta in base all'osservazione delle perdite e dei ritardi nei sistemi terminali. (Metodo adottato da TCP)

Quindi nel TCP si osservano:
- La quantità di Ack duplicati $\leftrightarrow$ Pacchetti persi.
- La quantità di timeout $\leftrightarrow$ Lunghi ritardi.

Il mittente quindi per __controllare__ la congestione usa una variabile chiamata __congestion window__ (CWND).
Questa insieme al valore della receive window definisce la dimensione della finestra di invio, cioè la dimensione della finestra sarà uguale al minimo dei due valori.
- ($dimensione\space della\space finestra=min(rwnd,cwnd)$)

Per __rilevare__ la congestione si possono effettuare delle azioni che reagiscono a certi eventi quali:
- Ack duplicati
- Timeout
Quindi se gli Ack arrivano __in sequenza__ e con una __buona frequenza__, allora si può inviare e __incrementare__ la quantità di segmenti inviati.
Invece se si presentano Ack __duplicati__ e/o __timeout__, allora è necessario __ridurre__ la finestra dei pacchetti che si spediscono senza aver ricevuto riscontri.

Si dice per questo che il protocollo TCP è __auto-temporizzante__, cioè che reagisce in base ai riscontri che ottiene.

Quindi l'idea è quella di incrementare il rate di trasmissione se non c'è congestione e diminuire se c'è congestione.
Per fare ciò si usa un algoritmo di controllo della congestione.
Tale algoritmo si basa su tre componenti:
- __Slow start__.
- __Congestion avoidance__.
- __Fast recovery.__

#### Slow start (Incremento esponenziale)

(Si ricorda che CWND sta per congestion window)

Funzionamento:
- Si parte da un valore di CWND inizializzata a $1\space MSS$, cioè $1$ maximum segment size.
- SI aumenta di $1\space MSS$ per ogni Ack ricevuto, quindi è __esponenziale__ in quanto se si mandano $x$ pacchetti, torneranno $x$ Ack, e quindi al prossimo invio si avrà $2x\space MSS$.
- La dimensione della finestra viene aumentata finchè non si raggiunge una soglia chiamata slow start threshold (ssthresh).
- Al primo timeout di un pacchetto si cambia alla componente chiamata __congestion avoidance__.

#### Congestion avoidance (Incremento lineare)

Funzionamento:
- Si incrementa il valore di CWND di $1$ ogni volta che si riceve __un blocco di Ack__ e non più per singolo Ack. Cioè ogni volta che viene riscontrata l'intera finestra di segmenti spediti e non il singolo segmento allora si aumenta di $1$ la CWND.
- L'incremento lineare continua finchè non si rileva un sintomo della congestione, ovvero un timeout o $3$ Ack duplicati.
- Al timeout il valore di ssthresh viene cambiato alla metà della CWND raggiunta e il valore di CWND a $1$.

#### Fast recovery (Usato nella versione TCP Reno)

Funzionamento:
- Si incrementa il valore di CWND di $1$ ogni volta che si riceve un Ack __duplicato__.
- Se avviene un __timeout__ si passa a slow start con il valore della CWND a $1$ e il valore di ssthresh alla metà del valore della CWND raggiunta prima del reset.
- Se si riceve un __nuovo Ack__ si passa a congestion avoidance con il valore della CWND che è uguale al valore di ssthresh.


#### Versioni di TCP

##### TCP Taho (o Tahoe)

Si parte con il __slow start__, il valore di CWND inizializzato a $1$ e il valore di ssthresh non definito.

Durante il controllo della congestione con la componente slow start, quindi con il valore di CWND raddopiato ad ogni RTT (Roundtrip time), se avviene un __timeout__ o $3$ Ack __duplicati__:
- Si riparte con una CWND a $1$ (quindi $1$ segmento come finestra) e si imposta il valore di ssthresh al valore della CWND raggiunto prima del reset diviso $2$.

Quando si sta in slow start e il valore di CWND raggiunge il valore di ssthresh allora si cambia la componente in __congestion avoidance__.

Durante la congestion avoidance, se avviene un __timeout__ o $3$ Ack __duplicati__:
- Si riparte con una CWND a $1$ e si imposta il valore di ssthresh al valore della CWND raggiunto prima del reset diviso $2$.

Quando si sta in congestion avoidance e accade un evento che causa il reset della CWND, si passa a slow start (con il nuovo valore per ssthresh).

![|750](https://i.imgur.com/tXkDrfO.png)

##### TCP Reno

È un affinamento della versione Tahoe in quanto si differenzia la reazione tra i due eventi che indicano congestione perché effettivamente sono causati da situazioni differenti:
- $3$ Ack duplicati indicano la capacità della rete di consegnare qualche segmento.
- Un timeout prima di $3$ Ack duplicati è __più allarmante__ in quanto non sono arrivati nemmeno i segmenti.

Quindi si reagisce in modo __meno drastico__ nel caso dei $3$ Ack duplicati:
- Si cambia componente in __fast recovery__.

È come il TCP Tahoe, ma quando avviene l'evento di $3$ Ack __duplicati__, sia se da slow start, sia se da congestion avoidance, si passa a fast recovery con il valore della CWND uguale al valore di $ssthresh+3$ (il valore di sshtresh è quello nuovo) e con il valore di ssthresh alla metà del valore di CWND.

![|750](https://i.imgur.com/HM249rW.png)

### Impostare il tempo per il timeout

Il timeout deve dipendere dal roundtrip time (RTT).
Si deve dare tempo al segmento per arrivare a destinazione e all'Ack di ritornare.

Per impostare il valore del timeout si deve:
- Stimare il RTT
- Far variare il valore del timeout in base al RTT

Si considera quindi il __SampleRTT__:
- È il tempo misurato dalla trasmissione del segmento fino alla ricezione dell'Ack
- Varia in base alla congestione nei router e carico nei sistemi terminali.
Serve quindi una stima più livellata di RTT.

Si considera quindi il __EstimatedRTT__:
- È il tempo stimato del RTT aggiustato attraverso dei pesi.
- Si calcola usando la formula:$$EstimatedRTT_{t+1}=(1-\alpha)\cdot EstimatedRTT_{t}+\alpha\cdot SampleRTT_{t+1}$$
- Solitamente $\alpha$ prende un valore tipico di $0.125$.
- $\alpha$ serve per assegnare minore peso alle misure recenti che a quelle più vecchie.
- Serve comunque avere un __margine di sicurezza__ per il timeout (un pacchetto singolo può far sbalzare di molto).

Si considera quindi il __DeviationRTT__:
- Si calcola usando la formula:$$DevRTT_{t+1}=(1-\beta)\cdot DevRTT_{t}+\beta\cdot|SampleRTT_{t+1}-EstimatedRTT_{t}|$$
- Solitamente $\beta$ prende un valore tipico di $0.25$.

A questo punto si può impostare il __valore del timeout__:
- Si imposta un valore iniziale pari a $1$ secondo.
- Se avviene un timeout si raddoppia.
- Appena viene ricevuto un segmento e aggiornato EstimatedRTT, si usa la formula:$$TimeoutInterval=EstimatedRTT_{t+1}+4\cdot DevRTT_{t+1}$$
# Livello di rete

Il livello di rete si occupa dell'__instradamento__ dei datagrammi da un host origine a un host destinazione, e quindi si lavora sugli __indirizzi IP__.

Durante il viaggio che fa un pacchetto, questa per ogni nodo intermedio __risalirà__ lo stack protocollare fino al livello di rete, in quanto ogni router deve capire qual'è il prossimo router a cui deve __inoltrare__ il pacchetto.
Quindi nei router non c'è:
- Il livello applicazione.
- Il livello trasporto.

## Funzioni chiave del livello di rete

### Instradamento (Routing)

L'instradamento determina il __percorso__ seguito dai pacchetti dall'origine alla destinazione, cioè attraverso quali router deve passare un pacchetto per raggiungere la destinazione data.

### Inoltro (Forwarding)

L'inoltro è l'atto di trasferire un pacchetto dalla porta di ingresso alla porta di uscita del router. La decisione su quale porta di uscita scegliere è stabilito dal routing.     

Quindi l'inoltro avviene all'interno del router.

Next hop: Prossimo router alla quale inviare un pacchetto

## Tabella di routing (o di forwarding)

Ogni router contiene una sua __tabella di routing__. Questa serve a decidere il prossimo router alla quale passare un pacchetto in base al valore nell'intestazione del pacchetto.

## Differenza tra switch e router

Un router è uno switch ma con delle funzionalità diverse.

### Packet Switch (Commutatore di pacchetto)

Uno __switch__ è un commutatore di pacchetto, cioè se riceve un pacchetto allora lo inoltra verso un altro commutatore.

È un dispositivo che si occupa del __trasferimento__ dall'interfaccia di input all'interfaccia di output, in base a un valore che è all'interno del campo di intestazione del pacchetto.

### Link-layer switch (Commutatore a livello di collegamento)

Un link-layer switch è un dispositivo che stabilisce l'inoltro di pacchetti in base al valore del campo presente nell'__intestazione del livello di collegamento__.

È utilizzato per collegare singoli computer all'interno di una rete LAN.

![|300](https://i.imgur.com/ZmQTFLG.png)

### Router 

Un router è un dispositivo che stabilisce l'inoltro di pacchetti in base al valore del campo presente nell'__intestazione del livello di rete__.

## Switching

Si possono avere due approcci:
- Approccio __a circuito virtuale__, che è un servizio orientato alla connessione, ovvero serve stabilire una connessione, in altre parole, riservare risorse, prima che i datagrammi possano viaggiare all'interno della rete.
	- A livello di rete significa stabilire a priori il percorso che sarà seguito da tutti i datagrammi.
- Approccio __a datagramma__, che è un servizio senza connessione, quindi non serve stabilire connessioni.
	- A livello di rete significa che ogni datagramma viaggia in modo indipendente dagli altri.

### Rete a circuito virtuale

Ogni pacchetto di un circuito virtuale ha un __numero VC__ chiamato __etichetta di circuito__ nella propria intestazione.

Durante il viaggio attraverso i router, ogni router sostituisce il numero VC del pacchetto che arriva con un nuovo numero.

### Rete a datagramma

I pacchetti vengono inoltrati utilizzando l'indirizzo dell'host destinazione, cioè per ogni router si va a guardare la sua __tabella d'inoltro__ e si confronta l'indirizzo IP del destinatario per capire a quale interfaccia di output bisogna inoltrare il pacchetto.

Il __confronto__ dell'indirizzo IP del destinatario è con dei __prefissi__ presenti nella tabella, e in quanto gli indirizzi IP sono numeri da $32\space bit$, si va a confrontare bit per bit, e la corrispondenza è sul prefisso uguale più lungo.
(Per utilizzare questo metodo serve avere continuità tra i prefissi)

## Architettura del router

Ogni router è costituito da:
- $N$ porte di input
- $N$ porte di output
- Lo switching fabric
- Il processore di routing

### Porta di input

Le porte di input implementano il livello fisico e il livello di collegamento.

È qui che i bit del pacchetto vengono ricostruiti a partire dal segnale ricevuto, e quindi una volta finita la ricostruzione, se il frame è integro lo si passa al livello di rete.

Nelle porte di input possono essere implementate le tabelle di routing per velocizzare il processamento dei dati. (Ritardo di elaborazione)

### Switching fabric

È una struttura che permette a un datagramma di commutare da una porta di input a una di output.

### Processore di routing

È la parte del router che implementa le funzionalità del livello di rete, quindi anche la parte del __table lookup__, cioè l'andare a controllare la tabella d'inoltro per capire a quale interfaccia di output spostare il datagramma.

### Porta di output

Nelle porte di output vengono accodati i datagrammi che vengono incapsulati in __frame__ e tradotti in __segnali__ da trasmettere attraverso il livello fisico.

## Ricerca nella tabella di routing

Per la ricerca della porta di uscita di un datagramma attraverso la tabella di routing, quest'ultima (la tabella) viene implementata utilizzando una __struttura ad albero__:
- Ogni livello dell'albero corrisponde a un bit dell'indirizzo di destinazione.
- Si confronta per bit partendo dalla radice, se $0$ allora si va nel sottoalbero di sinistra, se $1$ allora nel sottoalbero di destra.
Quindi la ricerca è in $N$ passi dove $N$ è il numero di bit nell'indirizzo.

## Tecniche di commutazione

Esistono $3$ tecniche di commutazione, cioè per fare passare un pacchetto dalla porta di input a quella di output:
- Tramite __memoria__, cioè si copiava il pacchetto all'interno della memoria, e dalla memoria lo si passava alla porta di output.
- Tramite __bus condiviso__, cioè le porte di ingresso trasferiscono il pacchetto direttamente alle porte di uscita tramite il bus, ma dato che è condiviso non possono transitare più pacchetti contemporaneamente.
- Tramite __crossbar switch (multipli bus)__, cioè sono presenti più bus e quindi è possibile trasferire più pacchetti contemporaneamente finché non trasferiscono su una stessa porta di output.

## Accodamento

L'accodamento può accadere sia nelle porte di __ingresso__ che nelle porte di __uscita__, e dipende dalla:
- Velocità di commutazione.
- Direzione del traffico.

La __velocità di commutazione__ è la frequenza alla quale il commutatore può trasferire pacchetti dalle porte di ingresso a quelle di uscita, e quindi si ha:
- Accodamento nelle __porte di ingresso__ quando la velocità di commutazione è inferiore alla velocità delle porte di ingresso, cioè quando fanno entrare più pacchetti di quanti ne si possono commutare.
- Accodamento nelle __porte di uscita__ quando la velocità di commutazione è superiore alla velocità delle porte di uscita e/o quando troppi pacchetti vengono __trasferiti__ sulla __stessa__ porta di uscita.

### Head-of-the-line blocking

Il __blocco in testa alla fila__ accade quando un pacchetto nella coda di ingresso che ha la propria porta di output libera, deve attendere il trasferimento del pacchetto in testa alla fila in quanto la sua porta di output è piena, andando a bloccarsi.

Quindi quando c'è troppo traffico verso una determinata porta, come conseguenza si può bloccare il traffico verso le altre porte libere.

## Protocolli del livello di rete

Il protocollo principale del livello di rete è il protocollo IP (Internet Protocol).

Altri protocolli del livello di rete sono:
- IGMP, che serve a gestire il multicasting.
- ICMP, che serve a gestire gli errori.
- ARP, che serve a mantenere l'associazione tra indirizzo IP e indirizzo MAC.
- DHCP (anche se è implementato a livello applicazione), che implementa funzionalità del livello di rete. È il protocollo che assegna a un host che entra all'interno di una rete, un indirizzo IP in maniera dinamica.

Sono presenti inoltre due protocolli di routing.

## Protocollo IP (IPv4)

Il protocollo IP non fa routing, ma fa forwarding.

È il protocollo responsabile:
- Della suddivisione in pacchetti.
- Del forwarding dei datagrammi
- Della consegna dei datagrammi al livello di rete, cioè prende un pacchetto da un host e lo fa arrivare a un indirizzo IP di destinazione (altro host).

È un protocollo:
- __Non affidabile__.
- __Senza connessione__, cioè non stabilisce connessioni per funzionare.
- __Basato su datagrammi__.

### Struttura del datagramma (Header del datagramma)

Il segmento del livello trasporto viene incapsulato insieme all'intestazione del datagramma del livello di rete.

Questa intestazione contiene:
- Sulla prima riga:
	- La versione del protocollo IP, se è __IPv4__ o __IPv6__.
	- La lunghezza dell'intestazione, in quanto un datagramma IP ha un numero variabile di intestazione, e quindi serve per indicare dove inizia il campo dati.
	- Il tipo di servizio, che serve per distinguere diversi datagrammi con requisiti di qualità del servizio diverse.
	- La lunghezza del datagramma, che serve per capire se il pacchetto è arrivato completamente.
- Sulla seconda riga:
	- L'identificatore, il flag e l'offset di frammentazione, questi $3$ campi servono per gestire la frammentazione dei pacchetti, spiegato più dettagliatamente [[qui]].
- Sulla terza riga:
	- TTL (Time-to-live), cioè il tempo di vita residuo, che diminuisce di $1$ ogni volta che viene elaborato in un router. E quando arriva a $0$, il datagramma viene scartato.
	- Il protocollo di livello superiore, che indica il livello di trasporto al quale va passato il datagramma. (Però include anche protocolli del livello di rete)
	- Checksum dell'intestazione, ricalcolata ad ogni router intermedio a causa del TTL e della frammentazione.
- Sulla quarta riga:
	- L'indirizzo IP dell'origine.
- Sulla quinta riga:
	- L'indirizzo IP della destinazione.
- Sulla sesta riga:
	- Dei campi opzionali come timestamp, registrazione dei percorsi e l'elenco dei router.
- Dopo la sesta riga:
	- Dati (incluso il segmento a livello di trasporto).

### Frammentazione (solo IPv4)

Un datagramma IP può passare attraverso __varie reti__, le quali potrebbero __non__ supportare una determinata lunghezza dei pacchetti.

Ogni router estrae il datagramma dal frame, lo elabora per poi incapsularlo in un nuovo frame.

Dato il __MTU__ (Maximum Transfer Unit), che è la __massima__ quantità di dati che un frame a livello di collegamento può trasportare, questa può __variare__ in base alla tecnologia di trasmissione presente nel router.
(e.g. di MTU: 1500b, 1492b)

Quindi può succedere che un datagramma IP può essere __frammentato__ in vari datagrammi IP di dimensioni più piccole che sono __indipendenti__, e che tocca al destinatario __riassemblare__ i frammenti prima di mandarli al livello di trasporto.

Per eseguire la riassemblazione vengono usati questi bit dell'intestazione IP, che quindi servono per identificare e ordinare i frammenti:
- Campo dell'identificazione, che serve per identificare tutti i frammenti di un determinato datagramma originale, in quanto assegnato in partenza dal host origine al momento della creazione del datagramma.
- Campo del flag, formato da $3\space bit$.
	- Il __primo__ bit è riservato (non usato).
	- Il __secondo__ bit indica se il datagramma può essere frammentato ($1$) o non ($0$).
	- Il __terzo__ bit indica se il datagramma è un frammento intermedio ($1$) o è l'ultimo frammento ($0$).
- Campo dell'offset, che specifica l'ordine del frammento all'interno del datagramma originario.

## Indirizzamento IPv4

Ogni interfaccia di un host ha un indirizzo IP, cioè se uno stesso host è collegato a una rete sia tramite Ethernet che interfaccia WiFi, allora avrà due indirizzi IP.

Quindi l'indirizzo IP __identifica l'interfaccia tra la rete e l'host__, e non dipende dall'host ma dalla rete.

Un router deve necessariamente avere più indirizzi IP, uno per ogni interfaccia, e tipicamente ne deve avere almeno $2$.

## Spazio degli indirizzi IP

Il numero totale degli indirizzi è $2^{32}$.

Solitamente si rappresentano in notazione:
- Binaria.
- Decimale puntata.
- Esadecimale, dove viene usata nella programmazione di rete.

## Gerarchia nell'indirizzamento

Ogni indirizzo IP è composto da un __prefisso__ e da un __suffisso__:
- Il prefisso individua la rete alla quale appartiene l'host che possiede tale indirizzo IP.
- Il suffisso individua un host tra i vari host che sono collegati alla stessa rete.

Ora il prefisso sarà identico per tutti quei host che sono collegati alla stessa rete, quindi la differenza all'interno di una rete è il suffisso.

La __lunghezza in bit__ del prefisso può essere:
- Fissa, se si fa l'indirizzamento con classi.
- Variabile, se si fa l'indirizzamento senza classi.

### Prefisso con lunghezza fissa

Il prefisso con lunghezza fissa può avere:
- $8\space bit$
- $16\space bit$
- $24\space bit$

Queste si distinguevano in __classi di indirizzo__:
- Quelli con $8\space bit$ appartengono alla classe A, e cominciano con $0$.
- Quelli con $16\space bit$ appartengono alla classe B, e cominciano con $10$.
- Quelli con $24\space bit$ appartengono alla classe C, e cominciano con $110$.
Inoltre ci sono altre due classi:
- Classe D, composta da indirizzi multicast, che cominciano con $1110$.
- Classe E, riservati per uso futuro, che cominciano con $1111$.

![|700](https://i.imgur.com/473CL1Y.png)

Uno dei principali vantaggi della lunghezza fissa è la facilità con la quale si può risalire alla classe e alla lunghezza del prefisso una volta individuato un indirizzo.
Inoltre sono molto facili da gestire.

D'altra parte il problema più grave è l'__esaurimento degli indirizzi__:
- La classe A può essere assegnata solo a $128$ organizzazioni al mondo, e ognuna può avere $16777216$ nodi (host collegati).
	- Quindi la maggiorparte degli indirizzi viene sprecata.
	- Poche organizzazioni potevano usufruire di indirizzi di classe A.
- La classe B ha gli stessi problemi della classe A.
- La classe C invece ha pochi indirizzi per rete.

### Prefisso con lunghezza variabile (Indirizzamento senza classi)

Con l'indirizzamento senza classi non si può più sapere quanti bit sono dedicati al prefisso e quindi al suffisso.
Per questo si usa la __notazione CIDR__ (Classless InterDomain Routing), che modifica la struttura dell'indirizzo:
- L'indirizzo IP rimane uguale.
- Viene aggiunto un numero $n$ per indicare il numero di bit assegnati alla prima parte dell'indirizzo (prefisso).
(e.g. $200.23.16.0/23$ è un indirizzo IP che ha i primi $23\space bit$ per il prefisso, e quindi $9\space bit$ per il suffisso)

## Range di un indirizzo IP

Dato $n$ la lunghezza del prefisso:
- Il numero di indirizzi per gli host di una rete è dato da $N=2^{32-n}$
- Per trovare il primo indirizzo si impostano a $0$ tutti i bit del suffisso.
- Per trovare l'ultimo indirizzo si impostano a $1$ tutti i bit del suffisso.

## Maschera di rete

La maschera di un indirizzo IP è un numero composto da $32\space bit$ in cui:
- I primi $n\space bit$ sono impostati a $1$
- Il resto $32-n\space bit$ sono impostati a $0$.

Attraverso la maschera si ottiene l'__indirizzo di rete__, che è usato nell'instradamento dei datagrammi verso la destinazione.

## Indirizzi IP speciali

Esistono degli indirizzi IP che sono speciali:
- $0.0.0.0$ è l'indirizzo dell'host stesso.
- Tutti $0$ per il prefisso e numeri per il suffisso indica un host all'interno della rete alla quale si appartiene, in quanto gli indirizzi IP che hanno lo $0$ come __numero di rete__ (prefisso) si riferiscono alla rete corrente.
- L'indirizzo composto da tutti $1$ permette la trasmissione __broadcast__ sulla rete locale.
- L'indirizzo composto da un numero di rete e poi tutti $1$ nel campo host permette l'invio di pacchetti broadcast a reti distanti.
- Gli indirizzi che cominciano con $127$ per i primi $8\space bit$ sono riservati al __loopback__, cioè i pacchetti inviati vengono elaborati localmente (scendono nello stack protocollare e risalgono) e trattati come pacchetti in arrivo.

## Ottenimento di un indirizzo IP per un host

Quando un host si connette a una rete, la rete assegna a quel host un indirizzo IP.

L'indirizzo assegnato a un host può essere fisso o temporaneo (dinamico).

Gli indirizzi temporanei vengono assegnati in base al __DHCP__.

## Protocollo DHCP (Dynamic Host Configuration Protocol)

Il protocollo DHCP __gestisce__ l'insieme degli indirizzi IP.

Ha come obiettivo l'__assegnazione dinamica__ di un indirizzo IP della rete.

È un __programma__ di tipo __client/server__ di livello applicazione:
- Quando un host si collega alla rete parte un client DHCP nel host.
- Esiste nella rete un server attivo che risponde alle richieste DHCP dei client.

Quando un host vuole entrare a far parte di una rete, ha bisogno di:
- Indirizzo IP.
- Maschera di rete.
- Indirizzo del router.
- Indirizzo DNS.

Il protocollo DHCP si basa su $4$ tipi di __messaggi__ (si ricorda che è un protocollo del livello applicazione):
- DHCP discover.
- DHCP offer.
- DHCP request.
- DHCP Ack.
e utilizza i servizi forniti dal protocollo UDP a livello trasporto fornendo come porta sorgente la $68$ per i server DHCP mentre come porta destinazione la $67$ per gli host.
### Formato messaggi DHCP

I campi importanti all'interno del messaggio DHCP sono:
- Opcode, che identifica se l'operazione è una richiesta o una risposta.
- Transaction ID, che è un numero intero impostato dal client e ripetuto dal server.
- Client IP address, che è l'indirizzo IP del client, impostato a $0$ se il client non lo conosce.
- Your IP address, che è l'indirizzo IP del client, inviato dal server.
- Server IP address, che è l'indirizzo IP del server, impostato a un indirizzo IP di broadcast (Solitamente tutti 1, quindi 255.255.255.255) se il client non lo conosce.

### Esempio di richiesta IP dal client

Un client che si collega a una rete deve:
- Inviare un messaggio DHCPDISCOVER:
	- Con un Transaction ID impostato dal client.
	- Con un Source address impostato a $0.0.0.0$ in quanto non ha un indirizzo IP
	- Con un Destination address impostato a $255.255.255.255$ in quanto non conosce l'indirizzo IP del server alla quale fare la richiesta, e quindi invia un messaggio broadcast (cioè a tutti quanti i nodi) nella rete.
Il server DHCP che sta in attesa di una richiesta riceve il messaggio broadcast e lo elabora mentre gli altri host lo ignorano. Quindi il server:
- Invia un messaggio DHCPOFFER:
	- Con un Transaction ID uguale alla richiesta ricevuta.
	- Con un Your address proposto dal server al client.
	- Con un server address che è se stesso, quindi lo inserisce.
	- Con un source address che è se stesso, quindi lo inserisce.
	- Con un destination address che è ancora broadcast, quindi $255.255.255.255$
Il client riceve l'offerta:
- Invia una risposta DHCPREQUEST:
	- Con un source address che è quello offerto da __uno__ dei server che ha offerto un indirizzo IP.
	- Con un destination address ancora in broadcast perché così va a notificare __tutti__ i server che gli hanno offerto un indirizzo IP.
Il server finisce con un Ack:
- Invia un messaggio DHCPACK:
	- Con un destination address ancora in broadcast.

### Porta per il client nota

Il protocollo DHCP usa porte well-known sia per il client ($68$) che per il server ($67$) perché:
- La risposta del server è broadcast, quindi si potrebbe avere il caso in cui due processi su host diversi potrebbero aver scelto la stessa porta effimera.
- Quindi usando una porta well-known si va a ecludere quel caso.

### Altre informazioni (Maschera, server DNS, router)

Il server invia solamente l'indirizzo IP al client, e il client per ottenere le altre informazioni:
- Esegue un trasferimento file FTP con il server su un path contenuto all'interno del messaggio DHCPACK per ottenere il file con le informazioni mancanti.

## Sottorete

Una sottorete è una rete __isolata__ i cui punti terminali sono collegati all'interfaccia di un host o di un router.
(È una parte della rete che viene sezionata attraverso l'aggiunta di una maschera di sottorete)

![|500](https://upload.wikimedia.org/wikipedia/commons/0/0b/Divisione_dei_bit_Host.png)

## Indirizzi privati

Alcuni blocchi di indirizzi sono stati resi privati:
- $10.0.0.0$ - $10.255.255.255$ (Notazione CIDR: $10.0.0.0/8$)
- $172.16.0.0$ - $172.31.255.255$ (Notazione CIDR: $172.16.0.0/12$)
- $192.168.0.0$ - $192.168.255.255$ (Notazione CIDR: $192.168.0.0/16$)

Gli indirizzi privati __non__ possono essere utilizzati nell'Internet pubblica, ma solamente all'__interno__ delle reti LAN.

Questi indirizzi, in quanto privati, possono essere usati da molte reti (diversi host con stesso indirizzo privato tra varie reti LAN), e quindi non si possono avere pacchetti in rete che hanno questi indirizzi IP come sorgente.

Per mandare sulla rete pubblica richieste generate da host con indirizzi privati e ricevere indietro risposte si adotta la __traduzione__ degli indirizzi di rete (NAT).

## NAT (Network Address Translation)

Il NAT gestisce la __conversione__ (traduzione) degli indirizzi da privato a pubblico e viceversa.

Basta un indirizzo pubblico per la NAT per ogni rete LAN.
Ciò però necessita l'uso di un altro valore per identificare ogni host all'interno della rete, in quanto se si usa un solo indirizzo pubblico, si deve identificare di chi è il pacchetto.

### Traduzione degli indirizzi di rete (NAT)

Quando un router NAT della rete LAN riceve un datagramma generato da un host interno:
- Va a cambiare nel datagramma:
	- L'indirizzo sorgente (privato) $\to$ nell'(unico) indirizzo pubblico del router.
	- Il numero di porta $\to$ in un numero temporaneo libero scelto dal router.

Il router dopo aver modificato correttamente il datagramma, lo inoltra nella rete.
Dalla rete ritornerà al router un datagramma di risposta per quello inviato.

Quando il router riceve il datagramma di risposta:
- Va a cambiare nel datagramma di risposta:
	- L'indirizzo di destinazione $\to$ all'indirizzo privato del host che deve ricevere la risposta.
	- Il numero di porta temporaneo scelto dal router $\to$ nel numero di porta che l'host aveva inserito nel datagramma.
- Lo invia al host che ha quel indirizzo privato.

Il router riesce a ricordarsi le informazioni da modificare al ritorno in quanto mantiene al suo interno una __tabella di traduzione NAT__ che contiene il mapping delle coppie di informazioni $(IP,numero\space di\space porta)$ sia per il lato LAN (privato) che per il lato WAN (esterno).

La procedura è molto rapida quindi non comporta rallentamenti o colli di bottiglia.

## Forwarding dei datagrammi IP

Il forwarding è l'azione di inoltrare, cioè collocare il datagramma sul giusto percorso.
Per giusto percorso si intende una serie di hop a dei router che porteranno il datagramma fino a destinazione.

Un host invia al router della sua rete locale il datagramma da inviare, e il router a sua volta quando riceve un datagramma da __inoltrare__, accede alla __tabella di routing__ per trovare il __successivo__ hop (interfaccia) a cui inviarlo.

### Tabella di routing (o Tabella d'inoltro)

Le righe contenute nella tabella vanno da blocchi di indirizzi più specifici, ovvero con più bit a partire da sinistra, fino a blocchi di indirizzi meno specifici, ovvero con meno bit a partire da sinistra (quindi più generali).
L'ultima riga è sempre di __default__, ovvero se arriva un datagramma con un indirizzo di destinazione non contenuto nelle altre righe di blocchi di indirizzi, allora il suo hop successivo sarà quello definito dalla riga di default.

Quando arriva un datagramma a un router, il router:
- applica la prima maschera (confronta con la prima riga il datagramma) all'indirizzo di destinazione del datagramma.
	- Se l'indirizzo di destinazione è uguale all'indirizzo di rete nella riga, allora l'indirizzo del salto successivo e il numero di interfaccia collegato alla maschera vengono estratti dalla tabella e usati per inoltrare il datagramma.
	- Se non è uguale, si riprova fino all'ultima riga.

![|500](https://i.imgur.com/p46hLGq.png)

## Protocollo ICMP (Internet Control Message Protocol)

È un protocollo di segnalazione di errori.
Notifica gli errori nella rete e permette di far segnalare ai router delle condizioni particolari, quindi con questo protocollo i router possono creare e inviare pacchetti.

Viene quindi usato da host e router per scambiarsi informazioni a livello di rete:
- Rete di destinazione irraggiungibile.
- Host destinazione irraggiungibile.
- Protocollo destinazione irraggiungibile.
- Porta destinazione irraggiungibile.
- Rete destinazione sconosciuta.
- Host destinazione sconosciuta.
- Richiesta __echo__.
- TTL scaduto.

Ognuna di queste descrizioni sono identificati da un __tipo__ e __codice__ e sono contenute all'interno di messaggi ICMP.
Il protocollo ICMP è considerato parte di IP anche se usa IP per inviare messaggi ICMP.

### Ping

Il programma __ping__ si basa sui messaggi di richiesta e risposta __echo__ di ICMP.

### Traceroute

Il programma __Traceroute__ si basa su una serie di datagrammi IP verso una destinazione, ciascuno contenente un segmento UDP con un numero di porta __non utilizzato__.
Il primo datagramma ha $TTL=1$, il secondo ha $TTL=2$, ...
Quando l'n-esimo datagramma arriva all'n-esimo router:
- Il router __scarta__ il datagramma in quanto ha $TTL=0$.
- E __invia__ all'origine un messaggio di allerta ICMP (tipo $11$, codice $0$).
- Questo messaggio include il nome del router e il suo indirizzo IP.
Quando un segmento UDP arriva all'host di destinazione si __ferma__ l'invio di datagrammi in quanto l'host di destinazione restituisce un messaggio ICMP di porta __non raggiungibile__ (tipo $3$, codice $3$).
È progettato per bloccarsi quando l'origine riceve questo messaggio ICMP.


## Routing

Il routing si occupa di trovare il miglior percorso (path, route) e di inserirlo nella tabella di routing (o tabella di forwarding).

Quindi il routing __costruisce__ le tabelle mentre il forwarding le __usa__.

Il routing può essere di due tipi:
- Routing __intra-dominio__, cioè routing all'interno di una rete gestita da un ISP.
- Routing __inter-dominio__, cioè routing tra più domini.

Per fare routing serve usare dei algoritmi di instradamento.

### Algoritmo di instradamento con vettore distanza (Distance Vector - DV)

È un algoritmo __distribuito__, ovvero non c'è un punto di centralizzazione che gestisce l'algoritmo. Quindi ogni nodo (router) riceve informazioni dai nodi vicini e opera su quelle.
Inoltre è __asincrono__, cioè non richiede che tutti i nodi operino al passo con gli altri.

L'algoritmo di instradamento con vettore distanza si basa su:
- Equazione di Bellman-Ford.
- Concetto di vettore di distanza.
#### Equazione di Bellman-Ford

L'equazione dice che la distanza tra un nodo $x$ e un nodo $y$ è dato dal minimo valore tra tutti i percorsi che sono composti dal cammino dal nodo $x$ ai suoi vicini, più il cammino dal vicino al nodo $y$.

![|500](https://i.imgur.com/zukVYWL.png)

#### Vettore distanza

È un array monodimensionale.
Ogni nodo possiede il suo vettore distanza.

Ogni cella di un array di un nodo rappresenta il costo minimo per arrivare a ogni altro nodo a partire da quel nodo.

Ogni nodo della rete inizializza il proprio vettore distanza iniziale, inserendo informazioni che il nodo riesce a ottenere dai vicini immediati.

Per ottenere queste informazioni ogni nodo invia dei __messaggi__ di __hello__ attraverso le proprie interfacce. Così facendo ogni nodo scopre l'identità dei vicini e la propria distanza da ognuno di essi.

Dopo che ogni nodo ha inizializzato il proprio vettore, ne invia una copia ai suoi vicini, in modo tale da far aggiornare i loro vettori distanza attraverso l'uso dell'equazione di Bellman-Ford.

Questa operazione viene eseguita da ogni nodo ogni volta che aggiornadosi, cambia il suo DV (Distance Vector):
- Quindi se un nodo dopo essersi aggiornato da un messaggio inviato dal vicino, deve aggiornare il suo vettore distanza, allora lo notifica ai suoi vicini.
- Se invece dopo essersi aggiornato, __non__ aggiorna il suo vettore distanza, allora __non__ lo notifica ai suoi vicini.

Può capitare che si guasti un collegamento, allora:
- Il nodo $x$ vicino aggiorna il suo vettore distanza inserendo il valore $16$ (significa infinito nell'implementazione del vettore distanza) per il nodo $g$ raggiunto dal collegamento guasto. Dopo aver aggiornato il suo vettore distanza, manderà questo aggiornamento ai nodi vicini che può ancora raggiungere.
- Può capitare che un nodo vicino di $x$, detto $y$, abbia ancora il nodo $g$ raggiungibile e che mandi questa informazione al nodo $x$.
- A questo punto il nodo $x$ aggiornerà di nuovo pensando che possa raggiunge il nodo $g$ tramite il nodo vicino $y$, cosa che in verità non può in quanto il nodo $y$ pensa di poter raggiungere il nodo $g$ attraverso il nodo $x$.
- Si crea quindi un ciclo di aggiornamenti, dove il costo per raggiungere il nodo $g$ per entrambi i nodi $x$ e $y$ salirà lentamente, fino ad arrivare a $16$, ovvero infinito.

Per prevenire questi tipi di problemil si ricorre a:
- Split horizon, dove invece di inviare la tabella attraverso ogni interfaccia, ciascun nodo invia solo una parte della sua tabella tramite le interfacce.
- Poisoned reverse, dove si pone a $\infty$ il valore del costo del percorso che passa attraverso il vicino a cui si sta inviando il vettore.

### Protocollo RIP (Routing Information Protocol)

È un protocollo di routing __intra-dominio__ basato su un algoritmo a vettore distanza.

In questo protocollo la distanza viene misurata in __hop__, dove il numero massimo di hop, ovvero di salti tra un router e un altro, è $15$, in quanto il valore $16$ indica l'infinito.
Ogni salto (link) ha costo unitario (cioè $1$).

Dato che il valore massimo è $15$, questo protocollo viene usato solamente in reti di dimensioni piccole, e anche perché:
- Richiede un continuo invio di messaggi di aggiornamento, che comporta un overhead (cioè cose spedite sulla rete che non sono dati).
- È molto lento per far propagare le informazioni.

Le __tabelle di routing__ in questo protocollo sono composte da $3$ colonne:
- Rete di destinazione.
- Prossimo router.
- Costo (in hop).

Nel protocollo RIP, i router invece di inviare solamente i vettori di distanza, inviano l'__intero contenuto della tabella di routing__.

I router si inviano dei __messaggi__, in quanto il protocollo si basa su una coppia di processi client-server e sul loro scambio di messaggi.

Quando un nuovo router viene inserito nella rete:
- Invia una __RIP Request__ per ricevere immediatamente informazioni di routing.
e in risposta gli altri router:
- Inviano __RIP Response__.

Inoltre le RIP Response (o advertisements) vengono inviate __periodicamente__ ogni $30$ secondi.

Si evitano cicli attraverso l'uso dello Split horizon misto al Poisoned reverse:
- Si mette a infinito ($16$) il costo della rotta che passa attraverso il vicino a cui si manda il advertisement.

#### Struttura dei messaggi RIP

Ogni messaggio RIP è composto da una entry della tabella di routing.

![|500](https://i.imgur.com/QDaZXAs.png)

#### Timer RIP

Il protocollo utilizza $3$ timer per gestire l'invio dei messaggi:
- Tiimer periodico:
	- Controlla l'invio dei messaggi di aggiornamento.
	- Ogni $25$ - $35$ secondi.
- Timer di scadenza:
	- Regola la __validità__ dei percorsi, cioè se entro lo scadere del timer non si riceve un aggiornamento dal un vicino, allora il percorso a quel vicino viene considerato scaduto e il suo costo viene impostato a $16$.
	- Ogni $180$ secondi.
- Timer per garbage collection:
	- Quando le informazioni non sono più valide, il router continua ad annunciare il percorso con costo pari a $16$, e allora scadera del timer rimuove il percorso (link) dalla tabella.
	- Ogni $120$ secondi.

#### Implementazione di RIP

VIene implementato come applicazione che usa UDP sulla porta $520$, ma va a operare sulle tabelle di routing del livello di rete.

Attraverso un processo chiamato __routed__ esegue RIP, ossia mantiene le informazioni di instradamento e scambia messaggi con i processi routed nei router vicini.

### Algoritmo di instradamento con Link state (Dijkstra)

#### Link State

Lo stato di un link indica il costo associato a tale link, quindi se il costo è infinito significa che il collegamento (link) __non esiste__ o che è stato interrotto.

Ogni nodo deve conoscere i costi di __tutti__ i collegamenti della rete, e per fare ciò esiste un database che mantiene la mappa completa della rete.
Questo database è __unico__ per tutta la rete e ogni nodo della rete ne possiede una copia.
Il database viene rappresentato come una matrice.

Ogni nodo per conoscere i propri vicini e i costi dei collegamenti verso loro:
- Invia messaggi di hello su tutte le sue interfacce.

Ogni nodo che riceve questi messaggi di hello va a creare una lista chiamata __LS packet__,
dove si vanno a inserire le coppie: (vicino, costo).

Ogni nodo esegue un __flooding__ dei LSP (LS packet), cioè invia a tutti i vicini il proprio LSP, e a loro volta i nodi vicini ritrasmetteranno questi LSP (tranne a quello dalla quale l'ha ricevuto) se sono nuovi.

Quindi alla fine di questa operazione di flooding si verrà a creare il __Link state database__, ovvero una matrice che contiene tutti i costi da un nodo a un altro.


#### Algoritmo di Dijkstra

È l'algoritmo che calcola il cammino a costo minimo da un nodo chiamato origine verso tutti gli altri nodi della rete.

È un algoritmo __iterativo__, cioè dopo la k-esima iterazione del ciclo i cammini a costo minimo sono noti a k nodi di destinazione.

Per costruire l'albero a costo minimo utilizzando il LS database, ogni nodo deve eseguire l'algoritmo di Dijkstra:
- Ogni nodo sceglie se stesso come radice dell'albero.
- Ogni nodo applica l'algoritmo indipendentemente.

![|550](https://i.imgur.com/YwEoD2g.png)

Utilizzando l'algoritmo di Dijkstra su un grafo di nodi si ottiene questo procedimento:
![|550](https://i.imgur.com/ByLVHcV.png)

### Protocollo OSPF

È un protocollo __intra-dominio__ a stato del collegamento (link state).

Utilizza il __flooding__ di informazioni di stato del collegamento e l'algoritmo di Dijkstra per determinare i percorsi a costo minimo.

Oltre al flooding iniziale per costruire il LSDB (Link state database), il protocollo ne fa uso per:
- Inviare periodicamente (ogni $30$ minuti) messaggi OSPF all'intero sistema autonomo.
- Ogni volta che si verifica un cambiamento nello stato di un collegamento, il router manda informazioni di instradamento a tutti gli altri router.

#### Messaggi OSPF

I messaggi OSPF vengono trasportati direttamente in datagrammi IP usando il numero di protocollo $89$ nel campo IP protocol e sono:
- __Hello__, che viene usato dai router per annunciare la propria esistenza ai vicini che conosce.
- __Database description__, che viene usato in risposta ai messaggi Hello, e quindi solitamente usato quando un nuovo router si unisce alla rete e ha bisogno della sua copia del database.
- __Link-state request__, che viene usato per richiedere specifiche informazioni su un collegamento.
- __Link-state update__, che viene usato come messaggio usato dal protocollo per la costruzione del Link state database.
- __Link-state ack__, che viene usato come messaggio di riscontro ai Link-state update.

### Routing nell'Internet

L'Internet è composto da un insieme di __sistemi autonomi__.

#### Sistema autonomo (AS)
Un sistema autonomo (Autonomous system) è un ISP.
Ad ognuno di questi viene assegnato dall'ICANN un identificativo univoco composto da $16\space bit$.

Gli AS hanno diverse dimensioni e sono classificati in base al modo in cui sono connessi ad altri AS:
- __AS stub__, sono quelli che hanno un solo collegamento verso un altro AS e che __non__ consentono il transito di traffico attraverso di esso.
- __AS multihomed__, sono quelli che hanno più di una connessione con altri AS ma che __non__ consentono il transito di traffico.
- __AS di transito__, sono quelli che hanno più di una connessione con altri AS e che consentono il transito di traffico.

I router all'interno di uno stesso AS eseguono lo __stesso__ algorimo di routing intra-dominio (IGP, Interior Gateway Protocol).

Dato che diversi AS possono decidere di usare protocolli intra-dominio diversi, serve avere __un solo__ protocollo __inter-dominio__ che gestisce il routing tra il vari AS (EGP, Exterior Gateway Protocol).

I __router gateway__ (router di confine) sono router che mettono in comunicazione AS diversi e che quindi devono eseguire un protocollo aggiuntivo rispetto agli altri router non gateway.

### Algoritmo con path-vector (Path-vector routing)

Il routing Path-vector consente di trovare percorsi che non si basano sul costo minimo, ma bensì su condizioni (politiche e/o commerciali) decise dal AS.

Quindi ogni sorgente può scegliere il percorso che percorre in base a diverse politiche tipo:
- Minimizzare il numero di hop.
- Evitare alcuni nodi.

L'algoritmo è simile all'algoritmo a distance vector, ma vengono inviati percorsi invece che solo le destinazioni.
Ogni nodo quando riceve un path vector da un vicino, aggiorna il suo path vector applicando la sua politica invece del costo minimo.

### Protocollo BGP (Border Gateway Protocol)

È un protocollo a __path vector__, cioè a distance vector con percorsi.

Viene usato per determinare i percorsi per le coppie origine-destinazione che interessano più AS.

Questo protocollo permette a ciascun AS modi per:
- Ottenere informazioni sulla raggiungibilità delle sottoreti da parte di AS confinanti.

Il protocollo BGP quindi altro non fa che propagare informazioni che conosce, in quanto:
- Internamente ogni AS sa come instradare.
- Esternalmente gli AS non si sanno instradare.

Il protocollo BGP presenta __due versioni__:
- __eBGP__ (external), installato su tutti i router di confine.
- __iBGP__ (internal), installato su tutti i router.

I router di confine devono quindi eseguire i $3$ protocolli di routing:
- Routing intra-dominio
- eBGP
- iBGP
mentre tutti gli altri ne eseguono solamente $2$:
- Routing intra-dominio
- iBGP

#### eBGP

Data una coppia di router gateway di due AS differenti, queste si chiamano __peer BGP__ e si scambiano informazioni di instradamento attraverso connessioni __TCP__ usando la porta $179$.

Le connessioni TCP che fanno transitare questi messaggi eBGP sono chiamati __sessioni BGP__.

Tramite i messaggi eBGP i router gateway prendono conoscenza di come instradare i pacchetti destinati ad altri AS, ma non basta perché:
- I router di confine sanno instradare pacchetti solo ad AS vicini.
- Nessuno dei router non di confine, anche se vicino a un router di confine (all'interno di uno stesso AS), sa come instradare un pacchetto destinato alle reti che si trovano in altri AS.
La soluzione a questi problemi è data dalla versione iBGP del protocollo.

#### iBGP

Attraverso iBGP si viene a creare una sessione tra ogni possibile coppia di router all'interno di un AS.

Tramite queste sessioni i router di confine di uno stesso AS andranno a propagare le informazioni ottenute tramite eBGP agli altri router dello stesso AS.
Questi scambi di messaggi continuano finché non ci sono più aggiornamenti.
Le informazioni vengono combinate e inviate anche ad altri AS, che poi verranno usate per creare le __tabelle dei percorsi__. (NON sono tabelle di routing)

![|500](https://i.imgur.com/hJlUF9t.png)

Queste tabelle vengono __inserite__ nelle tabelle di routing intra-dominio generate da RIP o OSPF:
- Nel caso di AS stub, l'unico router di confine dell'AS aggiunge una regola di default alla fine della sua tabella di routing e definisce come prossimo router quello che si trova dall'altro lato della connessione eBGP.
- Nel caso di AS di transito, il contenuto della tabella di percorso viene inserito nella tabella di routing ma bisogna impostare anche il relativo costo.

#### Attributi del percorso e rotte BGP

Quando un router annuncia una rotta per un prefisso (di rete) per una sessione BGP, va a includere anche un certo numero di __attributi BGP__:
- Prefisso + attributi = "rotta".

Due degli attributi più importanti sono:
- __AS-PATH__, che serve per selezionare i percorsi.
	- Elenca gli AS attraverso i quali è passato l'annuncio del prefisso.
- __NEXT-HOP__, è l'indirizzo IP dell'interfaccia su cui viene inviato il pacchetto.

Quando un router di confine riceve un annuncio di una rotta, utilizza le sue politiche d'importazione per decidere se accettare o rifiutare di utilizzare quella rotta.

Un router può ricavare più di una rotta verso una destinazione, ovvero ha percorsi multipli, e deve quindi sceglierne una. Per fare ciò segue delle regole di eliminazione:
- Alle rotte viene assegnato come attributo un valore di __preferenza locale__. E quindi si scelgono le rotte con i valori più alti di preferenza locale (ciò riflette la politica imposta dall'amministratore di rete).
- Si seleziona la rotta con valore AS-PATH più breve.
- Si seleziona quella il cui router di NEXT-HOP ha costo minore.

##### Esempio di annuncio
1) $A$ annuncia il percorso $Aw$ a $B$ e a $C$.
2) $B$ sceglie di non annunciare $BAw$ a $C$.
3) Quindi $C$ instraderà solo $CAw$ per raggiungere $w$.

#### Messaggi BGP

I messaggi BGP vengono scambiati attraverso protocollo TCP e sono:
- __OPEN__, che apre la connessione TCP e autentica il mittente.
- __UPDATE__, che annuncia il nuovo percorso (o cancella quello vecchio).
- __KEEPALIVE__, che mantiene la connessione attiva in mancanza di UPDATE.
- __NOTIFICATION__, che riporta gli errori del precedente messaggio, usato anche per chiudere il collegamento.


### Routing Unicast

È una comunicazione tra __una__ sorgente e __una__ destinazione.

### Routing Broadcast

È una comunicazione da __una__ sorgente a __tutti__ i nodi della rete.
Si effettua inserendo nell'indirizzo IP destinazione l'indirizzo broadcast di destinazione.

Una comunicazione broadcast è un __flooding__, e lo si può eseguire come:
- __Uncontrolled__ flooding, cioè quando un nodo riceve un pacchetto broadcast, lo duplica e lo invia a tutti i nodi vicini (escluso quello dalla quale ha ricevuto il pacchetto).
	- Se il grafo ha cicli, una o più copie del pacchetto cicleranno all'infinito nella rete.
- __Controlled__ flooding, che ha due possibili implementazioni.
	- Attraverso l'uso di numeri di sequenza e di liste che mantengono la cronologia dei pacchetti broadcast già ricevuti, duplicati e inoltrati.
	- Attraverso l'uso di uno __spanning tree__, quindi in modo tale che ogni nodo riceverà solamente una copia del pacchetto. Serve quindi costruire prima uno spanning tree della rete.

### Routing Multicast

È una comunicazione da __una__ sorgente a __un gruppo__ di destinazioni (almeno uno).
Queste destinazioni possono essere in reti differenti.

Una prima implementazione potrebbe essere l'invio di unicast multipli, ma questa implementazione è inefficiente e aggiunge ritardi vari.

Quindi viene invece implementato attraverso l'invio di un solo datagramma che viene duplicato dai router.

#### Indirizzamento nel routing Multicast

Dato che attraverso il routing Multicast è possibile comunicare con host multipli che appartengono a reti diverse, è necessario definire un indirizzo di destinazione che sia comune a tutti gli host del gruppo in quanto l'indirizzo IP di destinazione può essere solo uno.

Quindi viene utilizzato l'__indirizzo multicast__, questo indirizzo andrà a individuare il gruppo e tutti i suoi partecipanti.

Questi indirizzi multicast possono essere solamente all'interno del blocco di indirizzi a loro riservato, che è in IPv4: $224.0.0.0/4$

Un host che appartiene a un gruppo ha un indirizzo multicast __separato__ e __aggiuntivo__ rispetto al suo indirizzo IP primario.

Serve ora identificare quali host all'interno della rete appartengono a un gruppo, e quindi sono necessari due protocolli per il multicast:
- Uno per raccogliere le informazioni di appartenenza ai gruppi.
- Uno per diffondere le informazioni di appartenenza.

### Protocollo IGMP (Internet Group Management Protocol) (Routing Multicast)

È un protocollo che lavora tra un host e il router che gli è direttamente connesso.

Offre agli host il mezzo per informare i router ad essi connessi del fatto che un'applicazione in esecuzione vuole aderire a uno specifico gruppo multicast.

Questi messaggi inviati dagli host sono incapsulati in datagrammi IP con TTL impostato a $1$ (viene eliminato dopo il primo router/hop).

#### Messaggi IGMP

I messaggi IGMP sono:
- __Membership query__, che serve ai router per determinare a quali gruppi hanno aderito gli host su ogni interfaccia. (questo messaggio viene inviato periodicamente)
- __Membership report__, che serve agli host per informare i router su un'adesione, anche quando non sono mandati in seguito a una Membership query.
- __Leave group__, che serve agli host per informare i router quando lasciano un gruppo.

#### Albero di instradamento multicast

I pacchetti multicast vengono inviati tramite "alberi" che collegano tutti i partecipanti del gruppo.

È possibile avere un solo albero di instradamento che viene condiviso da tutto il gruppo multicast dove un router agisce da rappresentante del gruppo.

È possibile avere anche un albero per ciascuna origine nel gruppo multicast.

## IPv6

È il protocollo successivo al protocollo IPv4, nato in quanto:
- Lo spazio di indirizzi IPv4 non basta.
- Serve riprogettare/rivedere alcuni protocolli ausiliari come [[Reti di elaboratori#Protocollo ICMP|ICMP]].
- Serve ridisegnare il formato dei datagrammi.

Quindi:
- Gli indirizzi IP nel protocollo IPv6 sono lunghi $128\space bit$.
- Sono stati introdotte nuove opzioni e possibilità di estensioni.
- È stato progettato un nuovo formato header IP.
- Possiede una maggiore efficienza.
	- Non si frammentano più i datagrammi nei nodi intermedi.

L'adozione del protocollo IPv6 è lenta a causa di altre soluzioni come:
- Protocollo DHCP.
- Protocollo NAT.

### Formato dei datagrammi IPv6

![|550](https://i.imgur.com/IaIGzIk.png)

### Dual stack

Durante la transizione da IPv4 a IPv6 gli host devono poter comprendere entrambi i protocolli per la comunicazione in rete.

Per determinare quale versione utilizzare per inviare un pacchetto basta usare il DNS, in quanto ci restituisce l'indirizzo IP alla quale inviare il pacchetto, e questo indirizzo sarà o un indirizzo IPv4 o un indirizzo IPv6.

### Tunneling

È la tecnica da utilizzare quando due host IPv6 in comunicazione devono passare attraverso un regione (di nodi) IPv4.

Si incapsula il datagramma IPv6 nel blocco dati (payload) di un datagramma IPv4 creato appositamente, e si inseriscono come IP sorgente e destinazione gli estremi del tunnel, che è la regione IPv4.

![|550](https://i.imgur.com/nX2WPpi.png)

### Traduzione dell'intestazione

È la tecnica da utilizzare quando un host IPv6 vuole comunicare con un host IPv4.

Viene effettuata la traduzione nel router che sta tra le due regioni IPv6 e IPv4, per poi viaggiare dalla regione IPv4 fino alla destinazione IPv4.

# Livello di collegamento

La comunicazione a livello di collegamento non è __host-to-host__ come i livelli sopra ad esso, ma bensì __nodo-to-nodo__.

Al livello di collegamento:
- Gli host e i router vengono chiamati __nodi__ o __stazioni__.
- I pacchetti che transitano lungo i collegamenti vengono chiamati __frame__.

I canali di comunicazione che collegano nodi adiacenti lungo un cammino, detti __collegamenti__ o __link__, possono essere:
- Cablati.
- Wireless.
- LAN.
e questi collegamenti possono essere utilizzati in due modi:
- Collegamento __punto-punto__, cioè un collegamento dedicato a due soli dispositivi.
- Collegamento __broadcast__, cioè un collegamento è condiviso tra varie coppie di dispositivi.

## Servizi offerti dal livello di collegamento

Data la sostanziale differenza tra i vari tipi di collegamento, i servizi erogati dai protocolli del livello di collegamento __possono essere differenti__:
- Non tutti i protocolli forniscono un servizio di consegna affidabile.

I servizi che vengono offerti sono:
- __Framing__, cioè l'incapsulamento dei datagrammi del livello di rete all'interno di frame.
	- Si usano gli indirizzi MAC, cioè delle schede di rete, per indirizzare i frame.
- __Consegna affidabile__, è basata sugli Ack ed è considerata __non__ necessaria nei collegamenti ad alta stabilità, come la fibra ottica.
- __Controllo di flusso__.
- __Controllo degli errori__, causate da interferenze, ovvero altri segnali che si vanno a sommare al segnale in transito.
	- Vengono individuati tramite strumenti come bit di controllo.
	- Serve quindi correggere il frame in caso di errori.

## Implementazione del livello di collegamento

Il livello di collegamento viene implementato nei nodi attraverso le __interfacce di rete__:
- Scheda Ethernet.
- $802.11$.

Queste interfacce implementano anche il livello fisico.

## Sottolivelli del livello di collegamento

Le funzionalità del livello di collegamento sono suddivise in __due sottolivelli__:
- __Data-Link Control__ (DLC), che implementa tutte quelle funzioni che sono indipendenti dalla tecnologia usata (collegamenti punto-punto o broadcast).
	- Framing.
	- Controllo del flusso.
	- Controllo degli errori.
	- Rilevamento degli errori.
	- Correzione degli errori.
- __Media Access Control__ (MAC), che si occupa di gestire le collisioni, cioè il MAC controlla l'accesso al canale per cercare di __ridurre al minimo__ le collisioni.

## Errori al livello di collegamento (Data-Link Control)

Gli errori sono causati da interferenze che possono cambiare la forma del segnale, l'interferenza viene chiamato __rumore__.

Solitamente l'errore è su un sottoinsieme di bit invece che su un singolo bit, in quanto la durata dell'interferenza è più lunga rispetto a quello di un singolo bit.

Per rilevare questi errori si fa uso di bit di parità, con la quale si possono rilevare errori anche su singoli bit.

## Protocolli di accesso multiplo (Media Access Control)

Esistono due tipi di collegamenti di rete:
- Collegamento punto-punto.
	- Viene usato il protocollo Point-to-Point (PPP) del DLC.
- Collegamento broadcast.
	- Ethernet tradizionale (10Mbps).
	- Wireless LAN $802.11$ (WiFi).
	- Data la possibilità di collisioni è necessario l'uso di un protocollo per la gestione del canale condiviso (MAC).

Le __collisioni__ si generano quando i nodi ricevono due o più frame contemporaneamente.

Quindi i protocolli di accesso multiplo hanno lo scopo di fissare le modalità con cui i nodi regolano le loro trasmissioni sul canale condiviso.

I protocolli inoltre sono __decentralizzati__:
- Non ci sono nodi master.
- Non vi è una sincronizzazione dei clock.
e si possono classificare in una di tre categorie:
- Protocolli a suddivisione del canale.
- Protocolli ad accesso casuale.
- Protocolli a rotazione.

## Classificazione dei protocolli MAC

![|550](https://i.imgur.com/QiTwl0V.png)

### Protocollo a suddivisione del canale (Channel partitioning)

Questi tipi di protocolli vanno a suddividere un canale in parti più piccole, dove la suddivisione è su:
- Slot di tempo.
- Frequenza del canale.
- Codice.
per poi allocarle a un nodo per utilizzo esclusivo.

Con questo metodo è __impossibile__ avere collisioni.

#### TDMA (Time Division Multiple Access) (Protocollo a suddivisione del canale)

Protocollo a suddivisione del canale in __intervalli di tempo__:
- Gli slot non usati rimangono inattivi.
- No possibilità di collisioni.
- Non è flessibile. (Aumentano i nodi)

#### FDMA (Frequency Division Multiple Access) (Protocollo a suddivisione del canale)

Protocollo a suddivisione del canale in __bande di frequenza__:
- Gli slot non usati rimangono inattivi.
- No possibilità di collisioni.

#### CDMA (Code Division Multiple Access) (Protocollo a suddivisione del canale)

È un protocollo dove un solo canale occupa l'intera ampiezza di banda e dove tutte le stazioni possono inviare contemporaneamente pacchetti.

Tale protocollo funziona attraverso l'uso di __codici__ che vengono assegnati alle stazioni. Ogni stazione ha il proprio codice, che utilizza quando deve spedire dati sul canale condiviso, moltiplicando i dati per il codice prima di trasmetterli.

I codici sono anche chiamati __chip__, e sono in pratica delle sequenze di numeri.
- E.g. un chip $c_{1}$ è $[+1\space +1\space +1\space +1]$.
- O anche $[+1\space +1\space +1\space -1]$.

I codici hanno le seguenti proprietà:
- Se si moltiplica un codice $c_{i}$ per un altro codice $c_{j}$ si ottiene $0$.
- Se si moltiplica un codice $c_{i}$ per se stesso si ottiene il __numero delle stazioni__ del canale.

Attraverso queste due proprietà, una stazione $x$ per ricevere dati da una stazione $y$ sul canale:
- Va a moltiplicare i dati ricevuti per il codice del mittente.
- E in seguito lo divide per il numero delle stazioni.

I dati ricevuti possono essere:
- $-1$, significa che è un bit $0$.
- $+1$, significa che è un bit $1$.
- $0$, significa che non è un bit, quindi silenzio.

Per generare le sequenze di chip viene usata una __tabella di Walsh__ (una matrice quadrata).

In questa tabella __ogni riga è un codice__, cioè un chip.

Quindi se $W_{1}$ indica una sequenza con un chip solo (con una riga o una colonna) e può assumere valore $+1$ o $-1$, conoscendo $W_{N}$ si può creare $W_{2N}$ nel seguente modo:

![|500](https://i.imgur.com/ET3ZCIV.png)

e continuando ad applicare questa regola si ottiene:

![|500](https://i.imgur.com/mIJuVxf.png)

dove le righe di $W_{2}$ e $W_{4}$ sono sequenze di chip per reti con $2$ e $4$ stazioni.

### Protocollo ad accesso casuale (Random access)

Questi tipi di protocolli permettono a ogni stazione (nodo) di trasmettere quando hanno da trasmettere e imettono sul canale in modo casuale.

È possibile che si verifichi una collisione, e se accade, i nodi coinvolti ritrasmettono ripetutamente i pacchetti.

Ogni volta che una stazione (nodo) possiede dei dati da inviare, procede a inviare usando una procedura definita dal protocollo per decidere se spedire o meno.

Le stazioni quindi competono l'una con l'altra per accedere al canale condiviso.

Per controllare/gestire le collisioni, i protocolli ad accesso casuale definiscono:
- Come rilevare un'eventuale collisione.
- Come ritrasmettere se si è verificata una collisione.

#### ALOHA Puro (Protocollo ad accesso casuale)

È la prima versione del protocollo ALOHA, dove ogni stazione può inviare un frame tutte le volte che ha dati da inviare.

Una volta che il ricevente riceve correttamente il frame, invia indietro un Ack per notificare il mittente della corretta ricezione.

Se il mittente non riceve indietro questo Ack entro un __timeout__, allora deve ritrasmettere il frame.
Questo periodo di timeout equivale al massimo ritardo di propagazione di round-trip (andata del frame e ritorno dell'ack) tra le due stazioni più lontane.

Ora se due stazione ritrasmettono contemporaneamente di nuovo ci sarà una collisione, allora per non andare in loop, si attende un tempo random sempre più alto(__back-off__) prima di effettuare la ritrasmissione.
La casualità del back-off abbassa la probabilità di altre collisioni.
Quindi il back-off è un valore casuale che dipende dal numero di trasmissioni fallite, cioè:$$Backoff\space time=T\cdot R$$
dove:
- T è il tempo per inviare un frame.
- R è un valore randomico scelto in un intervallo da $0$ a $2^k-1$.
	- $k$ è il numero di tentativi.


Nel peggiore dei casi, dopo un numero massimo di tentativi la stazione interrompe i suoi tentativi di ritrasmissione per provare più tardi.

##### Esempio calcolo back-off e timeout

lorem ipsum

#### Slotted ALOHA (Protocollo ad accesso casuale)

È una versione progettata per aumentare l'efficienza di ALOHA che consiste nel dividere il tempo in __intervalli discreti__, ciascuno corrispondente a un frame time ($T_{fr}$).

Serve inoltre avere i nodi __sincronizzati__, cioè devono essere d'accordo nel confine fra gli intervalli, implementato facendo emettere da un'attrezzatura speciale un breve segnale all'inizio di ogni intervallo.

I pacchetti trasmessi sul canale hanno tutti la __stessa dimensione__.
Il tempo è suddiviso in slot dove ogni slot equivale al tempo di trasmissione di un pacchetto.
In questo modo i nodi iniziano la trasmissione dei pacchetti solamente all'inizio degli slot.
Quindi anche se in uno slot due o più pacchetti collidono, i nodi coinvolti rilevano l'evento prima del termine dello slot e proveranno a ritrasmettere con probabilità $p$ il loro pacchetto durante gli slot successivi.

Questa versione del protocollo ALOHA presenta miglioramenti in quanto:
- Il tempo di vulnerabilità si riduce a un solo slot ($T_{fr}$)
ma allo stesso tempo:
- Una certa frazione degli slot presenterà collisioni (Sprecati)
- Un'alta frazione degli slot rimane vuota, quindi inattiva.

#### CSMA (base) (Protocollo ad accesso casuale)

Il CSMA (Carrier Sense Multiple Access) è un protocollo che si mette ad ascoltare il canale prima di trasmettere (Carrier Sense).

Se rileva che il canale è libero, allora trasmette l'intero pacchetto, invece se il canale sta già trasmettendo, allora il nodo aspetta un altro intervallo di tempo.

Le collisioni possono comunque verificarsi in quanto il __ritardo di propagazione__ fa sì che due nodi non rilevino la reciproca trasmissione, quindi:
- Il tempo di vulnerabilità è pari al tempo di propagazione.
Inoltre anche la __distanza__ influenza la probabilità di collisione.

#### CSMA/CD (CSMA Collision Detection) (Protocollo ad accesso casuale)

È la versione del CSMA che si mette ad ascoltare il canale anche durante la trasmissione.
In questo modo il nodo rileva la collisione in poco tempo, riducendo il tempo di vulnerabilità, e quando lo rileva annulla la trasmissione.

La rilevazione della collisione è facile da implementare nelle LAN cablate ma è difficile nelle LAN wireless in quanto presenta un __costo energetico__ non trascurabile, soprattutto per i dispositivi che usano collegamenti wireless, in quanto a batteria.

Il mittente per far funzionare il Collision Detection, deve poter rilevare la trasmissione mentre sta trasmettendo, ovvero prima di inviare l'ultimo bit del frame.
Quindi il __tempo di trasmissione__ di un frame deve essere almeno __due volte__ il __tempo di propagazione__.

##### Metodi di persistenza

Un nodo che deve trasmettere pacchetti sul canale, si mette in ascolto sul canale, se lo trova __libero__:
- O trasmette subito con zero o una ritrasmissione se rileva una collisione (non persistente/1-persistente).
- Oppure trasmette con probabilità $p$ (p-persistente).

Invece se trova il canale __occupato__:
- O il nodo __desiste__ e decide di riascoltare dopo un tempo random (non-persistente).
- Oppure __persiste__ e decide di rimanere in ascolto finché il canale non si libera (1-persistente/p-persistente se canale con time slot).

La tipologia 1-persistente indica che se il nodo nota che il canale è libero, allora con probabilità $1$, cioè assicurato, andrà a trasmettere sul canale.

In tutte e 3 le persistenze se vi è collisione si fa __back-off__. 

### Protocollo a rotazione (Token)

Questi tipi di protocolli presentano un __token__ (un pacchetto solitamente).
Il nodo che possiede il token può trasmettere, e dopo un certo evento questo token viene trasferito al prossimo nel canale.

In questi protocolli i nodi che hanno molto da trasmettere sono avvantaggiati (non è fair).

#### Protocollo Polling

È un protocollo a rotazione dove un nodo principale sonda a turno gli altri per chiedere se hanno pacchetti da inviare.

Quindi questo protocollo:
- Non presenta collisione.
- Rimuove la possibilità di slot vuoti.
- Presenta un ritardo per il polling.
- Se si guasta il nodo principale, l'intero canale diventa inattivo.

#### Protocollo Token-Passing

È un protocollo a rotazione dove un __messaggio di controllo__ (token) circola fra i nodi seguendo un ordine prefissato.

Quindi questo protocollo:
- È decentralizzato (non c'è la presenza di un nodo principale/master).
- È altamente efficiente.
- Se si guasta un nodo l'intero canale diventa inattivo.

## Indirizzi MAC

Quando un datagramma viene incapsulato in un frame, all'interno dell'intestazione del frame sono contenuti gli indirizzi di collegamento della sorgente e destinazione del frame, cioè gli indirizzi del nodo attuale e quello del prossimo hop lungo il collegamento.

Ogni indirizzo MAC è composto da $48\space bit$ rappresentati in esadecimali.

Quando si vuole trasmettere un pacchetto a tutti i nodi della rete, lo si può fare attraverso l'__indirizzo MAC broadcast__, che è $FF-FF-FF-FF-FF-FF$.

> [!NOTE] Posizione dei campi degli indirizzi MAC nell'intestazione
> Il campo per l'indirizzo MAC di destinazione è posto prima del campo per quello della sorgente perché in questo modo non vi è bisogno di utilizzare risorse per frame non destinati a loro. Ciò è stato progettato proprio perché esistono gli indirizzi broadcast.

### Risoluzione degli indirizzi MAC

Un nodo per determinare l'indirizzo di collegamento MAC del prossimo hop usa il protocollo ARP.

### Protocollo ARP (Address Resolution Protocol)

È il protocollo che permette a ogni nodo di avere una __tabella ARP__ con la quale può conoscere il mapping tra l'indirizzo IP e l'indirizzo MAC di un nodo nella rete LAN.

![|500](https://i.imgur.com/ppCEnRQ.png)

Tali tabelle non vengono autoconfigurate ma vengono aggiornate con il mapping man mano che vengono scoperte.

Quindi se un nodo $A$ vuole inviare un datagramma a un nodo $B$, e l'indirizzo MAC di $B$ non è presente nella tabella ARP di $A$, allora $A$ andrà a trasmettere in un pacchetto __broadcast__ il messaggio di richiesta ARP, nella quale è presente l'indirizzo IP di $B$.
Quando $B$ riceve il pacchetto broadcast, andrà a rispondere ad $A$ tramite un pacchetto in __unicast__, e quindi $A$ potrà aggiornare la sua tabella ARP.

 Dalla tabella di routing viene restituito l'indirizzo IP del prossimo hop, che viene passato all'interno di una richiesta ARP, che restituirà l'indirizzo di collegamento del prossimo hop.

## Ethernet (LAN cablate)

È uno dei molteplici standard prodotte per le LAN, facente parte dello standard comune IEEE $802$. Nel caso specifico dell'Ethernet è $802.3$

Questi standard definiscono sia il livello fisico che quello di collegamento.

Esistono varie specifiche dell'Ethernet:
- Ethernet standard ($10Mbps$).
- Fast Ethernet ($100Mbps$).
- Gigabit Ethernet ($10Gbps$).

### Ethernet standard

Nata inizialmente quando si usava ancora un cavo coassiale come bus condiviso nella rete LAN.

#### Formato dei frame (Ethernet standard)

Presenta un __preambolo__ composto da $8\space byte$, delle quali $7$ che servono per attivare le interfacce di rete dei riceventi e per sincronizzare i loro orologi con quello del trasmittente, e il byte rimanente che delimita la fine del preambolo.
(__il preambolo fa parte dell'header del livello fisico__)

I campi dell'header del livello di collegamento invece sono:
- Indirizzo di destinazione.
- Indirizzo sorgente.
- Tipo per il multiplexing/demultiplexing, quindi che indica il protocollo del livello di rete.
- Dati (Payload) e padding se non si raggiunge una lunghezza minima di byte.
- CRC, che è un codice di controllo e serve alle interfacce per rilevare errori.

![|650](https://i.imgur.com/FfStUaD.png)

La lunghezza minima del frame ($64\space byte$) è necessario per il corretto funzionamento del CSMA/CD.

#### Funzionamento

Il protocollo funziona come per il CSMA/CD:
1) Framing, la scheda di rete (NIC) riceve un datagramma di rete dal nodo al quale è collegato e prepara un frame Ethernet.
2) Carrier sense e trasmissione, cioè ascolto del canale e trasmissione se è libero, invece se è occupato rimane in attesa.
3) Collision detection, si verifica durante la trasmissione la presenza di eventuali segnali proveniente da altre NIC, e si interrompe se sono presenti.
4) Jamming (nelle reti a bus condiviso), se si rileva una collisione allora invia un segnale di disturbo per avvisare gli altri NIC della collisione.
5) Back-off esponenziale.

### Fast Ethernet

È la versione aggiornata del Ethernet standard ed è retrocompatibile in quanto il sottolivello MAC è rimasto invariato, compreso il formato del frame e le sue dimensioni.

La velocità di trasmissione è cambiata invece da $10Mbps$ a $100Mbps$, ciò porta a problemi di funzionamento del CSMA/CD, in quanto il suo corretto funzionamento dipende dalla __velocità di trasmissione__, dalla dimensione minima del frame e dalla lunghezza massima della rete.

Quindi se si vuole mantenere la dimensione minima del frame a $512\space bit$ bisogna per forza __modificare la lunghezza massima della rete__:
- Se la velocità di trasmissione $10$ volte più veloce serve dover __rilevare le collisioni__ $10$ volte più velocemente, quindi la rete deve essere $10$ volte più corta.

Una prima soluzione è stata quella di cambiare __topologia__ (struttura dei collegamenti).
Invece di usare un singolo cavo come bus condiviso, si usano __repeater__ e __hub__.

Un hub è un ripetitore multi-porta, ovvero un dispositivo che opera sui singoli bit a livello fisico:
- Il bit all'arrivo del hub, viene riprodotto incrementandone il segnale e quindi lo ritrasmette attraverso tutte le sue altre interfacce.

Una seconda soluzione è quella di usare uno __switch__ al posto del hub.

Lo switch permette di:
- Filtrare e inoltrare i pacchetti Ethernet.
- Esamina l'indirizzo di destinazione e lo invia all'interfaccia corrispondente alla sua destinazione.
Grazie all'uso di switch si va a eliminare totalmente la possibilità di collisioni in quanto ogni host è collegato singolarmente allo switch.

Ora però serve avere una tabella di commutazione per lo switch per mantenere il mapping tra gli indirizzi MAC e le sue porte.

### Gigabit Ethernet

È la versione successiva al Fast Ethernet che va a $1000Mbps$.

Si utilizza una topologia a stella con switch.

#### 10 Gigabit Ethernet

È la versione a $10Gbps$ che usa collegamenti fisici in fibra ottica.
Adottato principalmente nelle MAN (Metropolitan Are Network).

### Switch

Gli switch che vengono usati in Ethernet hanno bisogno di mantenere la loro __tabella di commutazione__, che associa gli indirizzi MAC alle porte dello switch.

Uno switch crea inizialmente la sua tabella apprendendo quali nodi possono essere raggiunti attraverso determinate interfacce. Cioè quando riceve un pacchetto, lo switch impara l'indirizzo del mittente e registra la coppia mittente/interfaccia nella sua tabella.

Gli switch sono dispositivi __plug-and-play__, ovvero non richiedono intervento da parte dell'amministratore di rete o dall'utente, inoltre:
- Eliminano le collisioni.
- Interconnettono link eterogenei, cioè collega collegamenti che operano a diverse velocità.
- Aumentano la sicurezza della rete e migliorano il network management, in quanto non è più possibile fare __packet sniffing__.

### LAN virtuale (VLAN)

Le LAN virtuali sono LAN a livello logico e non fisico in quanto tutti i nodi sono collegati a un singolo switch.

Vengono usate per isolare il traffico e quindi gestire meglio la rete LAN.

Questo switch implementa tramite software le multiple LAN che quindi sono virtuali, e mantiene una tabella di associazioni porta/VLAN.

È possibile anche fare __daisy-chaining__ degli switch per avere più porte per le VLAN attraverso una porta configurata come __porta trunk__ per interconnettere i due switch.

![|600](https://i.imgur.com/xcqI8XP.png)

## Reti wireless

La categoria delle reti wireless comprende:
- LAN wireless (WLAN).
- Reti cellulari.
- Bluetooth.
- Reti di sensori.
- RFID.
- ...

Dato il diverso numero di reti sono presenti anche diversi standard per le reti wireless.

Gli elementi che compongono una rete wireless sono:
- Le stazioni base (base station/__Access Point__/AP), responsabili dell'imissione dei pacchetti ai host che sono collegati alla rete in modo wireless.
- I nodi che si collegano alle AP.
- Canale di trasmissione (wireless).

Il trasferimento dall'ambiente cablato al wireless dipende solamente dal livello di collegamento e fisico, in quanto serve solamente cambiare la scheda di rete per gli host e sostituire lo switch di collegamento con un AP.
Cambiano quindi solamente gli indirizzi MAC ma non quelli IP.

Esistono tipicamente due tipologie di LAN wireless:
- Rete con infrastruttura, dove i nodi si collegano a un AP che fornisce un servizio di base per il funzionamento della rete, per la trasmissione dei pacchetti e per il routing.
- Rete ad hoc, dove esistono solamente gli host (no AP), e quindi che si auto-organizzano per formare una rete per comunicare/trasferire informazioni tra di loro.
	- Ogni host in questo caso deve eseguire le funzionalità di rete quali network setup, routing e forwarding.

### Link wireless

I link wireless presentano caratteristiche particolari che influenzano la rete:
- __Attenuazione del segnale__, dove i segnali emessi diminuiscono rapidamente all'aumentare della distanza dal trasmettitore in quanto si disperdono in tutte le direzioni.
- __Propagazione multi-path__, ovvero quando i segnali vengono riflesse e/o assorbite su diversi superfici e/o oggetti causano una perdita di potenza e la possibilità di raggiungere punti di accesso (AP) attraverso percorsi multipli.
- Interferenze.

Quindi le interferenze sono il problema principale del segnale wireless, in quanto causano errori. Inoltre possono provenire sia dalla stessa sorgente che da altre sorgenti.

### Signal to Noise Ratio (SNR)

Se il rapporto tra il segnale e il rumore è alto, allora vuol dire che il segnale è più forte del rumore, e quindi è decodificabile.
Mentre se il rapporto è basso, allora il segnale è meno forte del rumore, e quindi i dati non possono essere recuperati.

### Controllo dell'accesso al mezzo

In quanto la rete wireless è a __mezzo condiviso__, è necessario controllare l'accesso al mezzo per evitare le collisioni.

La rilevazione della collisione è facile da implementare nelle LAN cablate ma è difficile nelle LAN wireless in quanto presenta un __costo energetico__ non trascurabile, soprattutto per i dispositivi che usano collegamenti wireless, in quanto a batteria.

L'uso del protocollo MAC CSMA/CD non è utilizzabile nelle reti wireless in quanto per rilevare le collisioni un host dovrebbe ascoltare il canale, e quindi il segnale ricevuto, ma poiché la potenza del segnale è inferiore rispetto a quello trasmesso dall'AP, si dovrebbe usare un adattatore di rete in grado di rilevarle, ma ciò costerebbe troppo in termini di efficienza energetica.

Inoltre esiste il problema del __terminal nascosto__ (Hidden terminal problem):
- Un nodo potrebbe non accorgersi che un altro nodo sta trasmettendo in quanto il raggio di trasmissione è limitato, come quello di rilevamento.
- Quindi se un nodo sta fuori il raggio di trasmissione di un altro nodo, questi penseranno in modo errato che il canale è libero in quanto non riescono a rilevarsi.
- Oppure è possibile che i due nodi stiano nel raggio di trasmissione ma comunque uno dei due non sente l'altro in quanto è "nascosto" a causa di ostacoli fisici.

### IEEE $802.11b$ (Wi-Fi) (Wireless Fidelity)

#### Architettura: BSS (Basic service set)

È una possibile architettura di una rete Wi-Fi, costituita da uno o più host wireless e da un access point(AP) collegato a sua volta in modo cablato o wireless a un router.

È possibile che una stazione si sposti tra diversi BSS, in tal caso l'indirizzo IP del nodo rimane lo stesso.
Ciò può accadere quando un nodo sente che il segnale da un AP si affievolisce e avvia una scansione per cercare un segnale più forte, trovando nel caso un altro AP con un segnale migliore.

#### Architettura: ESS (Extended service set)

È l'architettura che si viene a creare quando si collegano più BSS insieme.

I BSS sono collegati tramite un sistema di distribuzione che è una rete cablata o wireless.

![|550](https://i.imgur.com/AjNXfec.png)

#### Canali di uno spettro di rete

Lo spettro $2.4Ghz$ - $2.485Ghz$ è diviso in $11$ canali parzialmente sovrapposti.

Solitamente per cercare di non avere nessuna collisione, l'amministratore dell'AP sceglie di usare un canale lontano di almeno $4$ canali:
- Se un AP sta usando il canale $1$, un altro canale per non avere collisioni userà il canale $5$.

#### Associazione agli AP

Un nodo prima di potersi connettere a un AP disponibile in un BSS, ha bisogno di conoscere quell'AP, e quindi ha bisogno di eseguire un protocollo di associazione:
- Ogni AP invia periodicamente dei segnali chiamati __beacon__ che includono l'identificatore dell'AP e il suo indirizzo MAC.
- La stazione wireless che vuole entrare in un BSS scandisce tutti gli $11$ canali alla ricerca di frame di beacon e alla fine della scansione sceglie l'AP dalla quale ha ricevuto il beacon con la maggiore potenza di segnale e gli invia un frame con la richiesta di associazione.
- L'AP accetta la richiesta con un frame di risposta che permetterà all'host entrante di inviare una richiesta DHCP per ottenere un indirizzo IP.

### Protocollo MAC $802.11$ (CSMA/CA)

Per questo protocollo sono stati definiti due approcci per l'accesso al mezzo condiviso:
- __Distributed Coordination Function__ (DCF), in cui i nodi si contendono l'accesso al canale.
- __Point Coordination Function__ (PCF), in cui non c'è contesa e l'AP coordina l'accesso dei nodi al canale.

Il protocollo di accesso multiplo a carrier sense con evitamento delle collisioni (CSMA/CA)
differisce dal CSMA/CD in quanto cerca di __evitare le collisioni__ invece che cercare di __rilevarle__.

Alla base del protocollo vi è l'utilizzo degli Ack come feedback per capire se una trasmissione è andata a buon fine.

#### Spazio di interframe (IFS - Interframe Space)

Per evitare le collisioni un nodo si mette ad ascoltare il canale e comincerà a trasmettere solamente se sente libero il canale per un periodo di tempo chiamato __spazio di interframe__.

Ora questo spazio di interframe cambia in base al tipo di pacchetto che si deve spedire:
- __SIFS__, che dura meno del DIFS, ed è usato per finire una trasmissione.
	- Progettato per avere priorità su quelli che vogliono cominciare una trasmissione in quanto dura di meno del DIFS.
	- Usato dal destinatario per inviare l'Ack, e quindi deve avere priorità.
- __DIFS__, che dura più del SIFS, ed è usato per iniziare una trasmissione.
	- Usato dal mittente per inviare il pacchetto.

Quindi quando un mittente ascolta il canale per trasmettere un pacchetto, aspetta per un tempo pari a DIFS, e se durante questo intervallo il canale diventa occupato, allora il mittente
1) __Interrompe il conteggio__ del DIFS.
2) Aspetta che il canale torni __completamente libero__.
3) Una volta libero __riavvia da zero__ il conteggio del DIFS.

#### Finestra di contesa

Per evitare le collisioni, DIFS e SIFS __non__ sono sufficienti.
Quindi vi è anche una finestra di contesa, che è un intervallo di tempo da aspettare.

Dopo aver atteso un tempo IFS, se il canale è ancora libero, il nodo attende un ulteriore tempo che è la finestra di contesa (Contention window), questo per aggiungere un tempo randomico di attesa.

Quindi un nodo:
1) Attende un tempo IFS.
2) Comincia ad attendere un tempo randomico chiamato finestra di contesa, nella quale il tempo è __suddiviso in slot__ e a ogni slot si esegue il sensing del canale.
3) Se il canale è libero per la durata di uno slot, allora diminuisce il counter degli slot rimanenti prima di poter trasmettere.
4) Se il canale è occupato allora non diminuisce il counter degli slot e aspetta.
5) Quando il canale torna libero, __non riattende un tempo IFS__ ma riprende da dove aveva interrotto l'attesa della finestra di contesa.

Esiste anche la versione dove __si riattende un tempo IFS__ prima di riprendere l'attesa della finestra di contesa.

#### RTS/CTS

È un altro meccanismo per cercare di evitare le collisioni.

Dato il problema del __hidden terminal__, non risolvibile tramite IFS e finestra di contesa, è necessario questo meccanismo di prenotazione del canale:
- Request-to-send (RTS). (Astiene/blocca quelli vicini al mittente)
- Clear-to-send (CTS). (Astiene/blocca quelli vicini al destinatario)

Questo meccanismo serve più che altro per informare a tutti i vicini sia del mittente che del destinatario che devono astenersi dal trasmettere.

![|550](https://i.imgur.com/sSBGViD.png)

##### Problema della stazione esposta

Quando una stazione si astiene dall'usare il canale anche se potrebbe trasmettere in quanto non si verificherebbero collisioni.

#### Ack e timer dell'Ack

È necessario inoltre utilizzare riscontri positivi, ovvero Ack, e anche timer per capire se la trasmissione è andata a buon fine:
- Il mittente non può aspettare all'infinito l'Ack.
- Imposta quindi un timer chiamato Ack timeout.
- Se tale timer __scade senza aver ricevuto l'Ack__, il nodo suppone che la trasmissione __sia fallita__ e tenta una ritrasmissione.

#### Network Allocation Vector (NAV)

Le stazioni che non sono coinvolte nella trasmissione di una coppia mittente/destinatario, dato il meccanismo dei RTS/CTS, per sapere per quanto tempo doversi astenere dal trasmettere, viene letto un __campo__ presente all'interno dei __frame RTS/CTS__ dove si include la durata di tempo in cui il nodo mittente occuperà il canale per trasmettere il frame e ricevere l'Ack.

Quindi le stazioni che sono influenzate dai frame RTS/CTS avviano un __timer__ chiamato __NAV__ che indica quanto tempo devono attendere prima di eseguire il sensing del canale.

Ogni stazione __prima__ di ascoltare il canale verifica il NAV.

#### Formato del frame

![|700](https://i.imgur.com/GZNjxYQ.png)

- __Frame Control__ (FC), indica il tipo di frame.
	- RTS.
	- CTS.
	- Dati.
	- Ack.
- __D__, indica la durata della trasmissione, ovvero il NAV.
- __Indirizzi__, indicano gli indirizzi MAC.
- __SC__. (non visto)
- __Frame body__, contiene i dati di tutti i livelli sopra.
- __FCS__, è un codice per gli errori.

![|700](https://i.imgur.com/5cK8dYg.png)

Il Frame Control contiene molte informazioni utili:
- Protocol version.
- Tipo, che può essere:
	- $00$, indica che è un frame di __gestione__, usati per le comunicazioni iniziali tra le stazioni e gli AP.
	- $01$, indica che è un frame di __controllo__, usati per accedere al canale e dare riscontro.
	- $10$, indica che è un frame di __dati__, usati per trasportare dati.
- Sottotipo, indica che tipo che frame di controllo è:
	- $1011$ è RTS.
	- $1100$ è CTS.
	- $1101$ è Ack.

Sono presenti $4$ campi per gli indirizzi e vengono usati per gestire la connesione tra i nodi e gli AP.

![|700](https://i.imgur.com/AdCdL5T.png)

#### Mobilità all'interno della rete

Quando un nodo sente il segnale verso l'AP debole a causa di spostamenti verso una zona con segnale debole, avvia una nuova scansione per cercare un AP più vicino e quindi con un segnale migliore.

Il cambio di AP non comporta alcun problema ai livello sopra del livello di collegamento.

### Bluetooth

È una tecnologia LAN wireless progettata per connettere dispositivi con diverse funzioni.

Una LAN Bluetooth è una rete ad hoc, in quanto si forma senza la necessità di un AP.

Viene usata una banda da $2.4Ghz$ divisa in $79$ canali da $1Mhz$ ciascuno.

#### Piconet

È una rete piccola composta al massimo da $8$ dispositivi, di cui $1$ stazione primaria e $7$ secondarie che si sintonizzano con la primaria.

#### Scatternet

È una combinazione di Piconet.

Si viene a formare da una stazione secondaria di una Piconet che funge da primaria per un'altra Piconet.

#### Protocollo MAC: Bluetooth

La tecnologia Bluetooth usa TDMA (Time Division Multiple Access) con __slot temporali__ di $625 \mu s$. (Microsecondi)

Nel canale, la stazione primaria e le secondarie inviano e ricevono dati ma non contemporaneamente in quanto:
- La stazione primaria usa __slot pari__.
- Le secondarie usano in modo alterno gli __slot dispari__. (Se solo una stazione allora tutti gli slot dispari)

La durata effettiva della trasmissione dei dati __non__ dura $625\mu s$ ma circa $366\mu s$.
Il restante tempo è utilizzato per effettuare un __salto di frequenza__, cioè che ogni slot lavora su una frequenza diversa. (Anche per cambiare dallo stato di ricezione a quello di invio)

### RFID (Radio Frequecy Identification)

Gli elementi principali di una rete RFID sono:
- Una serie di tag, cioè delle etichette adesive che al loro interno presentano un microcircuito e un'antenna. All'interno del microcircuito è compresa della memoria, nella quale si possono memorizzare delle informazioni, che solitamente è un identificativo univoco.
- Un reader, ovvero un dispositivo che presenta delle antenne, che trasmette le richieste e riceve le risposte dai tag.
- Un server che gestisce i dati ricevuti dal reader e che lo processa.

I reader possono essere di due tipi:
- Fissi.
- Mobile.

I tag possono essere di due tipi:
- Attivi, ovvero presentano una forma di batteria.
- Passivi, cioè che __non__ presentano una forma di batteria.

I tag passivi, anche se privi di energia, funzionano tramite __backscattering__, cioè:
- Riflettono il segnale (l'energia) che ricevono dai reader.
- Ricevendo la trasmissione, sinergizza con essa.
- Riesce a fare un minimo di computazione locale necessaria per rispondere.
- Modifica il segnale ricevuto modulandola in base a quello che deve ritrasmettere al reader.

#### Identificazione dei Tag

Il canale tra il reader e i tag è broadcast.

Il reader quando invia un segnale:
- Se ritorna solo un segnale, ok.
- Se ritorna più di un segnale, il reader deve regolare l'accesso al canale.

#### Protocolli MAC per RFID

Per i dispositivi RFI sono presenti:
- Protocolli basati su albero.
- Protocolli basati su ALOHA.

##### Frame Slotted ALOHA (FSA)

Il canale è slotizzato:
- Tempo in slots.

Reader esegue richiesta per un frame.
Ogni Tag sceglie uno slot di tempo di quel frame e inserisce all'interno dello slot scelto un numero randomico che lo identifica.

##### Tree Slotted ALOHA (TSA)

Ogni collisione genera un nuovo nodo dell'albero dove si riprova il trasferimento, se ancora collisione si continua, se no collisione allora si passa al prossimo slot.

# Sicurezza

Un attacco è definito anche come __intrusione__, ovvero un qualsiasi insieme di azioni che tenta di compromettere uno o più proprietà tra queste:
- L'__integrità__, cioè il contenuto della comunicazione non deve essere alterato.
- La __confidenzialità__, cioè che solo il mittente e il destinatario devono essere in grado di comprendere il contenuto del messaggio.
- La __disponibilità__, cioè che gli utenti legittimi devono poter usare i servizi di rete in ogni momento.

## Programmi dolosi

I programmi dolosi come virus e worm possono introdursi all'interno degli host tramite vari metodi:
- Attachment.
- Programmi scaricabili.
- Sfruttando vulnerabilità di programmi già presenti negli host.

L'obiettivo di un attacco mira a creare un punto di appoggio per un futuro accesso tramite:
- Creazione di un account.
- Installazione di una __backdoor__.
oltre all'installazione di programmi dolosi e DDoS.

## Network mapping (Scansione della rete)

Durante la fase della scansione della rete, l'attaccante mira a recuperare più informazioni possibili sulla rete obiettivo.

È possibile effettuare questa fase attraverso strumenti come:
- Whois, dig, nslookup.
- Nmap (strumento di network mapping).

L'obiettivo è quello di __tracciare una mappa dei sistemi connessi__ e __individuarne le vulnerabilità__.

I metodi usati si differenziano in:
- Metodi basati su __richiesta valida__. (Messaggi "corretti" ma fasulli)
- Metodi basati su __richiesta non valida__. (Messaggi "errati" e fasulli)

I metodi basati su richiesta valida si suddividono ulteriormente in metodi che usano protocolli diversi:
- TCP.
	- Attraverso l'invio di TCP SYN e quindi ricevendo un TCP SYN/ACK.
	- Attraverso l'invio di TCP flag che causano il ritorno di un TCP RST.
- UDP.
- ICMP, largamente usato per i mezzi che offre nel verificare se una destinazione è raggiungibile.
	- Attraverso l'invio di ICMP echo request, cioè un ping.
	- Attraverso l'invio di ICMP timestamp request.
	- Attraverso l'invio di ICMP information request.
	- Attraverso l'invio di ICMP address mask request.

I metodi basati su richiesta non valida sfruttano le specifiche dei messaggi di errore di alcuni protocolli attraverso l'invio di messaggi "errati" per ricevere un messaggio di errore dalla macchina obiettivo:
- Invio di un primo frammento senza inviare i successivi.
	- La macchina ricevente dopo un timeout risponde con un ICMP fragment reassembly time exceeded.

## Port scanning (Identificazione delle vulnerabilità)

Durante la fase dell'identificazione delle vulnerabilità si mira a fare una scansione a livello di singoli host dei servizi disponibili su di essi.

I metodi usati per eseguire Port scanning sono simili a quelli del Network mapping.

## Tipi di attacchi

- Sniffing, ovvero spiare una comunicazione, capire che dati stanno venendo trasmessi.
- Spoofing, ovvero l'impersonare un altro soggetto.
- Hijacking, ovvero il dirottamento di una sessione in corso.
- DoS, ovvero il mettere fuori uso alcuni servizi.

## Contromisure

### Antivirus

Sono software usati per rilevare ed eliminare programmi dolosi.

Esaminano i dati interni al host e rilevano la presenza di programmi dolosi noti.

Analizzano il comportamento dei programmi, in particolare le istruzioni __sospette__ eseguite da queste.

Deve essere costantemente aggiornato con la creazione di nuovi attacchi.

### Firewall

È una struttura sia hardware che software che separa una rete privata dal resto dell'Internet.

Consente all'amministratore di controllare e gestire il flusso del traffico dati, quindi solamente a quello autorizzato sarà consentito passare.

Il filtraggio dei pacchetti si basa sulla tabella ACL, ovvero una tabella di regole da applicare ai pacchetti entranti.

### IDS (Sistema di intrusion detection)

È un sistema passivo che si basa sull'analisi del traffico di rete.

Genera allarmi quando rileva azioni quali:
- Scansione delle porte o TCP/IP
- Attacchi DoS

Si basa su un packet sniffer usati insieme a un insieme di regole.

#### Network based intrusion detection

Il sistema cattura e analizza il traffico di rete.

#### Anomaly based intrusion detection

Il sistema crea un profilo di traffico "normale" e genera un allarme quando rileva un comportamento di rete anomalo.

Può avere elevati falsi positivi e falsi negativi ma può rilevare nuovi attacchi.

## Sicurezza della comunicazione

- Crittografia.
- Hash.
- Firma digitale.
