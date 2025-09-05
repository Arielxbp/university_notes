___

## Internet routing

È il routing inter-dominio.

Data la dimensione dell'Internet, cioè il numero di router che compongono l'Internet, è praticamente impossibile usare un 
solo protocollo di routing.

Ogni ISP è un __sistema autonomo__ (AS).

Quindi solamente i router appartenenti a un __sistema autonomo__ utilizzano lo stesso protocollo di routing.

Ad ognun sistema autonomo viene assegnato un identificativo di $16\space bit$ chiamato autonomous number (ASN)

Gli AS hanno diverse dimensioni e sono classificati in base al modo in cui sono connessi ad altri AS:
- __AS stub__, sono quelli che hanno un solo collegamento verso un altro AS.
- __AS multihomed__, sono quelli che hanno più di una connessione con altri AS ma che __non__ consentono il transito di traffico.
- __AS di transito__, sono quelli che hanno più di una connessione con altri AS e che consentono il transito di traffico.

I router che collegano più AS devono implementare più di un protocollo per gestire il collegamento.

I protocolli di routing intra-dominio sono:
- RIP
- OSPF
mentre quelli inter-dominio sono:
- BGP


## Protocollo BGP (Border Gateway Protocol)

Il protocollo BGP permette a ciascuna sottorete di comunicare la propria esistenza al resto dell'Internet.

È un protocollo a __path vector__, cioè a distance vector ma con percorsi. Permette di scegliere i router da non usare per il transito dei pacchetti.

BGP presenta due versioni:
- eBGP (external), installato su tutti i router di confine.
- iBGP (internal), installato su tutti i router.

I router di confine devono quindi eseguire i $3$ protocolli di routing:
- Routing intra-dominio
- eBGP
- iBGP
mentre tutti gli altri ne eseguono solamente $2$:
- Routing intra-dominio
- iBGP

Il funzionamento di BGP viene implementato attraverso connessioni TCP sulla porta $179$.

I router di confine si connettono ad altri router di confine attraverso delle __sessioni eBGP__.
I messaggi scambiati durante queste sessioni eBGP servono per indicare ad alcuni router come instradare i pacchetti destinati ad alcune reti, ma le informazioni di raggiungibilità __non__ sono complete.

Nessuno dei router non di confine (all'interno di un AS) sa come instradare un pacchetto destinato alle reti che si trovano in altri AS.
Questo problema viene risolto dal iBGP.

Attraverso iBGP si viene a creare una sessione tra ogni possibile coppia di router all'interno di un AS.
Tramite queste sessioni avvengono gli scambi di messaggi per creare le tabelle dei percorsi (non sono tabelle di routing).
Queste tabelle vengono inserite nelle tabelle di routing intra-dominio:
- Nel caso di AS stub, l'unico router di confine dell'AS aggiunge una regola di default alla fine della sua tabella di routing e definisce come prossimo router quello che si trova dall'altro lato della connessione eBGP
- Nel caso di AS di transito, il contenuto della tabella di percorso deve essere inserito nella tabella di routing ma bisogna impostare il costo.

## Attributi del percorso e rotte BGP

Quando un router annuncia una rotta per un prefisso (di rete) per una sessione BGP, va a includere anche un certo numero di __attributi BGP__.

Un router può ricavare più di una rotta verso una destinazione, ovvero ha percorsi multipli, e deve quindi sceglierne una. Per fare ciò segue delle regole di eliminazione:
- Alle rotte viene assegnato come attributo un valore di __preferenza locale__. E quindi si scelgono le rotte con i valori più alti di preferenza locale (riflette la politica imposta dall'amministratore di rete).
- Si seleziona la rotta con valore AS-PATH più breve.
- ...

## Messaggi BGP

I messaggi BGP vengono scambiati attraverso protocollo TCP e sono:
- __OPEN__, che apre la connessione TCP e autentica il mittente.
- __UPDATE__, che annuncia il nuovo percorso (o cancella quello vecchio).
- __KEEPALIVE__, che mantiene la connessione attiva in mancanza di UPDATE.
- __NOTIFICATION__, che riporta gli errori del precedente messaggio, usato anche per chiudere il collegamento.



# Routing unicast, broadcast, multicast

## Unicast

È una comunicazione tra una sorgente e una destinazione.

## Broadcast

È una comunicazione da una sorgente a tutti i nodi della rete.
Si effettua inserendo nell'indirizzo IP destinazione l'indirizzo broadcast di destinazione.

Una comunicazione broadcast è un __flooding__, e si esegue come:
- Uncontrolled flooding, cioè quando un nodo riceve un pacchetto broadcast, lo duplica e lo invia a tutti i nodi vicini (escluso quello dalla quale ha ricevuto il pacchetto).
	- Se il grafo ha cicli, una o più copie del pacchetto cicleranno all'infinito nella rete.
- Controlled flooding, cioè non si forwardano pacchetti già ricevuti e inoltrati tramite l'uso di una lista dei pacchetti già ricevuti, duplicati e inoltrati.

Si usa uno __spanning tree__ per gestire i casi di pacchetti ridondanti.

Serve quindi prima costruire uno spanning tree della rete.

## Multicast

È una comunicazione da una sorgente a un gruppo di destinazioni.

Una prima implementazione potrebbe essere l'invio di unicast multipli, ma questa implementazione è inefficiente e aggiunge ritardi vari.
Quindi viene invece implementato attraverso l'invio di un solo datagramma che viene duplicato dai router.

È possibile definire dei gruppi di host ma che sono in reti diverse attraverso un __indirizzo multicast__ che identifica il gruppo.

I blocchi di indirizzi riservati per il multicast sono:
- In IPv4: 224.0.0.0/4

Sono necessari due protocolli per il multicast:
- Uno per raccogliere le informazioni di appartenenza ai gruppi.
- Uno per diffondere le informazioni di appartenenza.

## Protocollo IGMP

È un protocollo che lavora tra un host e il router che gli è direttamente connesso.
Offre agli host il mezzo per informare i router ad essi connessi del fatto che un'applicazione in esecuzione vuole aderire a uno specifico gruppo multicast.
Questi messaggi inviati dai host sono incapsulati in datagrammi IP, con IP protocolo number 2.

## Albero di instradamento multicast

È possibile avere un solo albero di instradamento che viene condiviso da tutto il gruppo multicast dove un router agisce da rappresentante del gruppo.

È possibile avere anche un albero per ciascuna origine nel gruppo multicast.


# IPv6

È il protocollo IP successore dell'IPv4, nato dalla necessità di:
- Aumentare lo spazio di indirizzi.

Con IPv6 si hanno indirizzi IP lunghi $128\space bit$, e una maggiore efficienza grazie anche alla rimozione della frammentazione.

Viene usato anche un nuovo formato per gli header IP.
\
IPv6 presenta la sua suite di protocolli:
- Una sua versione di protocollo ICMP
e va a rimuovere l'uso di protocolli come:
- NAT
- DHCP

## Dual stack

Durante la transizione da IPv4 a IPv6 gli host devono poter comprendere entrambi i protocolli per la comunicazione in rete.

Per determinare quale versione utilizzare per inviare un pacchetto serve usare il DNS, in quanto ci restituisce l'indirizzo IP alla quale inviare un pacchetto, e questo indirizzo che DNS restituisce sarà o un indirizzo IPv4 o un indirizzo IPv6.

## Tunneling

È la tecnica da utilizzare quando due host IPv6 in comunicazione devono passare attraverso un regione IPv4.

Il funzionamento è che si incapsula il datagramma IPv6 nel payload di un datagramma IPv4, e si inseriscono come IP sorgente e destinazione gli estremi del tunnel, che è la regione IPv4.

## Traduzione dell'intestazione

È la tecnica da utilizzare quando un host IPv6 vuole comunicare con un host IPv4.

Viene effettuata la traduzione prima che arrivi a destinazione.

