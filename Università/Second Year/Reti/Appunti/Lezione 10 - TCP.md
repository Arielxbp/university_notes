___

# Esonero

- Fino alla fine del livello trasporto
- Vale solo per giugno/luglio
- 

# Protocollo TCP

- È orientato al flusso di dati, cioè invia uno stream di byte continuo, che vengono raggruppati in un certo numero di byte detti segmenti.
- Un segmento è composto da un header e la parte per i dati
- All'interno del header sono presenti:
	- L'indirizzo della porta della sorgente
	- L'indirizzo della porta della destinazione
	- Il numero di sequenza è il numero che identifica il segmento, il TCP non assegna sequenzialmente i numeri di sequenza.
	- Il numero di riscontro è il numero che si riferisce al byte ricevuto(?)
	- La lunghezza dell'header
	- 6 bit riservati, non usati
	- 6 bit che sono flag: assumono certi significati quando sono 1. Se ack\==1 allora il segmento conterrà anche il ack

# Connessione TCP

- Il procedimento si suddivide in 3 fasi
	1) Apertura della connessione
	2) Trasferimento dei dati
	3) Chiusura della connessione

## Apertura della connessione

- La richiesta è un segmento senza dati che presenta il flag syn a 1
- Tale segmento presenta anche come numero di sequenza un random ISN, che viene usato dal server per rispondere
- La risposta del primo segmento viene dato con i flag syn+ack del server
- La risposta dal client alla risposta del server ha il flag ack per rispondere al server
- Solo dopo questi 3 segmenti si può dire che la connessione è aperta

## Trasferimento dei dati

- I segmenti di dati presentano i flag ack e push
- Esistono dati URG (urgenti) che vengono elaborati immediatamente indipendentemente dalla loro posizione nel flusso

## Chiusura della connessione

- Vi è uno scambio di segmenti simile a quello di apertura

# Numeri di sequenza e ACK di TCP

- Il numero di sequenza di ogni segmento è il numero del primo byte del segmento nel flusso di byte
- L'ACK è il numero di sequenza del prossimo byte atteso dall'altro lato

# Affidabilità del TCP

- Presenta Ack cumulativi
	- Dopo la ritrasmissione dei segmenti persi, il destinatario intanto ha ricevuto altri segmenti con numero successivo, dopo che riceve il segmento mancante che è stato ritrasmesso, manderà un Ack cumulativo che avrà il numero atteso più recente, cioè quello che deve inviare
- Timer associato al più vecchio pacchetto non riscontrato
- Ritrasmissione solamente del segmento all'inizio della coda di spedizione

- Se arriva il primo segmento avvio un timer, attendo per il tempo del timer il segmento successivo, se arriva ackko entrambi, sennò ackko solamente quello arrivato

- Se arriva un segmento con numero di sequenza maggiore di quello aspettato, si invia immediatamente un ack duplicato per richiedere la ritrasmissione

# Ritrasmissione dei segmenti

- Una volta inviato un segmento, il mittente si mantiene una copia del segmento inviato in una coda dove attente che gli ritorni il riscontro del segmento inviato.
- Se il segmento non viene riscontrato allora c'è un timer che allo scadere andrà a ritrasmettere il segmento
- Oppure se vengono ricevuti 3 Ack duplicati allora si andrà a ritrasmettere immediatamente il segmento senza attendere il timer

- In alcuni casi la perdita di Ack non causa la ritrasmissione dei segmenti

# Ri

- Utilizza la pipeline, cioè può inviare più segmenti alla volta senza aspettare per ognuno il riscontro
- Il numero di sequenza non è sequenziale
- Utilizza Ack cumulativi, cioè conferma tutti i byte precedenti a quello indicato
- Utilizza il timeout/timer, per la ritrasmissione
- Utilizza la ritrasmissione, è singola, cioè ritrasmette un solo segmento non riscontrato e non i successivi

- Esempio di es: Viene proposto un esempio di trasmissione TCP e si deve sapere che succede

# Controllo del flusso

- L'obiettivo è di bilanciare la velocità di invio con la velocità di ricezione
- Viene realizzato tramite il feedback ricevuto esplicitamente dal destinatario, che comunica al mittente lo spazio disponibile

- Uno degli campi presenti nel header è quello riservato alla dimensione della finestra
- L'apertura, chiusura e riduzione della finestra di invio è controllata dal destinatario
- La finestra di ricezione è segnalata dal valore di rwnd
- 