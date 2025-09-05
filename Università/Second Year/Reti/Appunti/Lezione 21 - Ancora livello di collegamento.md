___

## Wireless

Gli elementi di una rete wireless sono:
- Le stazioni base (base station), responsabili per mandare pacchetti ai host che sono collegati alla rete in modo wireless.
	- Sono chiamate __Access Point__ (AP)
- Gli host che permettono una connessione wireless.

Il trasferimento dall'ambiente cablato al wireless dipende solamente dal livello di collegamento e fisico, in quanto serve solamente cambiare scheda di rete per gli host e sostituire lo switch di collegamento con un AP.

## Reti ad hoc (senza infrastruttura)

È una rete composta da multipli host che si __auto-organizzano__ per formare una rete e comunicano liberamente tra di loro.

Ogni host deve eseguire le funzionalità di rete quali:
- Network setup.
- Routing.
- Forwarding.
- ..

## Reti wireless

Le reti wireless presentano caratteristiche particolari che influenzano la rete:
- Attenuazione del segnale, dove i segnali emessi diminuiscono rapidamente all'aumentare della distanza dal trasmettitore in quanto si disperdono in tutte le direzioni.
- Propagazione multi-path, ovvero quando i segnali vengono riflesse e/o assorbite su diversi superfici e/o oggetti causando una perdita di potenza e la possibilità di raggiungere punti di accesso (AP) attraverso percorsi multipli.
- Interferenze.

## Accesso al mezzo wireless

### Collision detection (non possibile)
L'uso del protocollo MAC CSMA/CD non è utilizzabile nelle reti wireless in quanto per rilevare le collisioni un host dovrebbe ascoltare il canale, e quindi il segnale ricevuto, ma poiché la potenza del segnale è inferiore rispetto a quello trasmesso dall'AP, si dovrebbe usare un adattatore di rete in grado di rilevarle, ma ciò costerebbe troppo in termini di efficienza energetica.

### Hidden terminal problem 
Inoltre un host potrebbe non accorgersi che un altro host sta trasmettendo e quindi non sarebbe in grado di rilevare la collisione mentre ascolta il canale.

## IEEE $802.11$ (Wi-Fi) (Wireless Fidelity)

### Architettura: BSS (Basic service set)

È una possibile architettura di una rete Wi-Fi, costituita da uno o più host wireless e da un access point(AP)

È possibile che una stazione si sposti tra diversi BSS, in tal caso l'indirizzo IP del nodo rimane lo stesso.
Ciò può accadere quando un nodo sente che il segnale da un AP si affievolisce e avvia una scansione per cercare un segnale più forte, trovando nel caso un altro AP con un segnale migliore.

### Architettura: ESS (Extended service set)

È l'architettura che include le BSS, quindi è costituita da due o più BSS.

I BSS sono collegati tramite un sistema di distribuzione che è una rete cablata o wireless.

### Canali e associazione

Lo spettro $2.4$Ghz - $2.485$Ghz è diviso in $11$ canali parzialmente sovrapposti.

Quindi sono possibili interferenze tra AP vicini con uno stesso canale.

L'associazione di un nodo a un AP ...

## Protocollo MAC $802.11$

Esistono due tecniche di accesso al mezzo condiviso:
- Distributed Coordination Function (DCF), in cui i nodi si contendono l'accesso al canale.
- Point Coordination Function (PCF), in cui non c'è una contesa del canale e l'AP coordina l'accesso dei nodi al canale.

### CSMA/CA (Collision Avoidance)

Serve evitare le collisioni, cioè quando due o più nodi trasmettono simultaneamente.

Serve avere un riscontro per capire se una trasmissione è andata a buon fine, cioè se non c'è stata collisione.
Si usa quindi l'Ack.

#### Spazio interframe

È uno spazio all'interno del canale che serve per gestire le collisioni.

Quindi un nodo, quando si mette in ascolto sul canale, se lo sente libero per DIFS tempo allora comincia a trasmettere.

Se invece durante l'intervallo di tempo DIFS il canale diventa occupato, allora il nodo aspetta che il canale torni completamente libero, e una volta libero ricomincia il conteggio del DIFS.

Per la congestion window si aspetta solamente il tempo rimanente. (Non si riparte da zero)

#### RTS/CTS

Dato il problema del __hidden terminal__, non risolvibile tramite IFS e finetra di contesa, è necessario un meccanismo di prenotazione del canale:
- Request-to-send (RTS). (Astiene/blocca quelli vicini al mittente)
- Clear-to-send (CTS). (Astiene/blocca quelli vicini al destinatario)

##### Problema della stazione esposta

Quando una stazione si astiene dall'usare il canale anche se potrebbe trasmettere in quanto non si verificherebbero collisioni.

#### Ack e timer dell'Ack

È necessario inoltre utilizzare riscontri positivi, ovvero Ack, e anche timer per capire se la trasmissione è andata a buon fine.

#### Network Allocation Vector (NAV)

Quando un nodo invia un frame, RTS include la durata di tempo in cui occuperà il canale per trasmettere il frame e ricevere l'Ack.

I nodi che sono influenzati da questo stop dato dal RTS/CTS avviano un timer chiamato NAV che indica quanto tempo devono attendere prima di eseguire il sensing del canale.

### Formato del frame

Il frame presenta diversi campi:
- Frame Control (FC), che indica il tipo di frame e include alcune informazioni di controllo.
	- Tipo (00,01,10)
		- 
- D, che indica la durata della trasmissione
- Indirizzi, indirizzi MAC
- SC, che include informazioni sui frammenti
- Frame Body, ovvero i dati dei livello sopra
- FCS, che è il codice CRC a $32\space bit$

### Indirizzamento

Le informazioni riguardanti l'indirizzamento è contenuto all'interno del campo FC

