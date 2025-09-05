
La comunicazione a livello di collegamento non è __host-to-host__ ma bensì __nodo-to-nodo__.

Al livello di collegamento:
- Gli host e i router vengono chiamati __nodi__ o __stazioni__.
- I pacchetti che transitano lungo i collegamenti vengono chiamati __frame__.

I protocolli implementati dal livello di collegamento si occupano del trasporto dei datagrammi lungo un singolo canale di comunicazione.

## Framing

Il datagramma proveniente dal livello di rete deve essere incapsulato nei frame, includendo un'intestazione del livello di collegamento.

## Consegna affidabile

È un servizio basato su Ack che viene utilizzato nei collegamenti soggetti a elevati tassi di errori come nei collegamenti wireless.

## Controllo di flusso

## Rilevazione degli errori

## Correzione degli errori

# Implementazione del livello di collegamento

Ogni host che possiede una scheda di rete implementa il livello di collegamento.

## Sottolivelli del livello di collegamento

Il __Data-Link Control__ è il sottolivello che si occupa di tutte le questioni comuni sia ai collegamenti punto-punto che a quelli broadcast.

Il __Media Access Control__ è il sottolivello che si occupa solo degli aspetti specifici dei canali broadcast.

## Errori al livello di collegamento

Gli erroi sono causati da interferenze che possono cambiare la forma del segnale.

Solitamente l'errore è su un sottoinsieme di bit invece che su un singolo bit, in quanto la durata dell'interferenza è più lunga rispetto a quello di un solo bit.

### Rilevamento degli errori

Attraverso l'utilizzo del bit di parità si possono rilevare errori su singoli bit.

## Collegamento punto-punto

Usa ethernet tra i nodi.

## Collegamento broadcast

Usa wireless LAN $802.11$ o Ethernet tradizionale.

Serve un protocollo per la gestione del canale condiviso.

## Protocolli di accesso multiplo

Questi protocolli servono a gestire la trasmissione condivisa tra multipli nodi su un singolo mezzo di comunicazione.

Si possono classificare in $3$ categorie:
- Protocolli a suddivisione del canale, questo suddivide un canale in slot più piccole e lo assegna a un nodo per utilizzo esclusivo.
- Protocolli ad accesso casuale, questo da l'accesso completo (non suddiviso) in modo casuale, quindi può comportare collisioni.
- Protocolli a rotazione, round-robin bruhh.

### Protocolli di suddivisione in canali

#### Protocollo TDMA

È un protocollo ad accesso multiplo a divisione di tempo.

Divide il canale in intervalli di tempo, dove ogni nodo ha un turno assegnato.

Ha il problema che gli slot non usati rimangono inattivi.

#### Protocollo FDMA

È un protocollo ad accesso multiplo a divisione del canale.

Divide il canale in bande di frequenza, dove a ogni nodo è assegnata una banda di frequenza prefissata.

Ha il problema che le bande non usate rimangono inattive.

### Protocollo ad accesso casuale

L'accesso è casuale, e ogni volta che un nodo ha dei dati da inviare, usa una procedura definita dal protocollo per deciderer se trasmettere o meno.

CSMA/CD = Ethernet
CSMA/CA = WiFi

#### Protocollo ALOHA

È un protocollo ad accesso casuale.

Ogni nodo può inviare un frame tutte le volte che ha dati da inviare.
Quando il destinatario riceve frame, va a inviare un Ack per notificare la corretta ricezione del frame.
Il mittente quindi presenta un valore per il timeout per aspettare l'Ack di ricezione.
Quando due nodi trasmettono contemporaneamente ci sarà collisione, allora si attende un tempo random chiamato __back-off__ prima di effettuare la ritrasmissione.
La casualità del back-off fa evitare altre collisioni.
Se dopo un numero massimo di tentativi di ritrasmissione k, il nodo non riesce a trasmettere, allora interrompe i suoi tentativi per riprovare più tardi.

È un protocollo molto inefficiente, in quanto si presentano elevate probabilità di collisione.
Questa probabilità è segnata dal __tempo di vulnerabilità__, cioè l'intervallo di tempo nel quale il frame è a rischio di collisioni.


> [!NOTE] Efficienza (throughput)
> L'efficienza è definita come la frazione di slot vincenti in presenza di un elevato numero N di nodi attivi.


#### Protocollo Slotted ALOHA

Un miglioramento del protocollo ALOHA consiste nel dividere il tempo in intervalli discreti, dove ciascuno corrisponde a un frame time.
Serve una sincronizzazione in quanto i nodi devono essere d'accordo nel confine fra gli intervalli.

#### Protocollo CSMA

È un protocollo ad accesso multiplo a rilevazione della portante.

Funziona che un nodo si pone in ascolto prima di trasmettere, se il nodo rileva che il canale è libero, allora trasmette l'interno pacchetto.
Invece se il canale sta già trasmettendo, il nodo aspetta un altro intervallo di tempo.

Il tempo di trasmissione di un frame deve essere almeno due volte il tempo di propagazione.

