___

# Controllo della congestione

- Quando si hanno varie sorgenti che trasmettono molti dati allo stesso tempo, la rete non è in grado di gestire questi dati
- La congestione della rete comporta vari problemi, quali pacchetti persi e lunghi ritardi
- Principalmente sono i nodi TCP intermedi a congestionarsi

## Finestra di congestione

- Per controllare la congestione si usano delle variabili riguardanti la dimensione della finestra di invio nella rete
- Dimensione della finestra quindi deve essere il minimo tra le due variabili

## Rilevamento della congestione

- Ack duplicati e timeout indicano perdite di dati, cioè rete congestionata
- Quindi TCP è auto-temporizzante, ovvero reagisce in basse ai riscontri che ottiene

## Controllo della congestione

- Incrementare il bitrate di trasmissione se non c'è congestione (Ack)
- Diminuire il bitrate di trasmissione se c'è congestione (segmenti persi)

# Slow start: Incremento esponenziale (Algoritmo)

- Slow start threshold, ssthresh
- È una soglia alla dimensione della finestra di congestione dell'algoritmo
- Esponenziale

# Congestion avoidance

- Per ogni roundtime trip si aumenta la variabile cwnd di uno

# TCP Tahoe (Versione di TCP)

- È una versione del TCP che utilizza la slow start e la congestion avoidance

# TCP Reno (Versione di TCP)

- Ottimizzazione attraverso il riconoscimento della differenza tra:
	- 3 Ack duplicati
	- Timeout
- Nel caso del timeout non è arrivato nessun pacchetto
- Nel caso degli Ack duplicati alcuni pacchetti sono arrivati
- Quindi nel caso del timeout, usando TCP Reno si riparte da 1 la congestion window (cwnd)
- Invece nel caso di 3 Ack duplicati, si entra nella fase di fast recovery, cioè si parte dal valore del ssthreshold+3

# Tempo di andata/ritorno e timeout

- Il valore di timeout non può essere né troppo piccolo né troppo grande.
- Il SampleRTT è il tempo misurato dalla trasmissione del segmento fino alla ricezione di Ack

# Esercizi sul livello trasporto

## Esercizio 2

- Un server TCP ha ricevuto e riscontrato all'interno di una connessione i byte fino al 4000. Dire quale azione esegue il server dopo i seguenti eventi:
	1) Il server riceve un segmento di 1000 byte con numero di sequenza pari a 3001
	2) In seguito all'evento 1 il server riceve un segmento di 1000 byte con numero di sequenza pari a 6001
	3) In seguito all'evento 2 il server riceve un segmento di 1000 byte con numero di sequenza pari a 5001
	4) In seguito all'evento 3 il server riceve un segmento di 1000 byte con numero di sequenza pari a 4001

- Risposta:
	1) Dopo 1 il server manda 

- Riscontrato 4000 -> server manda ack di 4001 (lo richiede),
- Arriva segmento pari a 3001 (byte dal 3001-4000) -> il server sa che è duplicato -> manda di nuovo ack di 4001 per richiederlo
- Arriva segmento pari a 6001 -> il server se lo piglia ma non ha ancora 4001 -> rimanda ack di 4001
- Arriva segmento pari a 5001 -> il server se lo piglia ma non ha ancora 4001 -> rimanda ack di 4001
- Arriva segmento pari a 4001 -> il server se lo piglia e ha tutto fino al 6001 -> manda ack cumulativo di 7001

## Esercizio 4

- Nel protocollo TCP la finestra di invio può essere più piccola, più grande o della stessa dimensione della finestra di ricezione?

- Risposta: più grande, e prende il min tra questo e la congestion window

## Esercizio 5

- L'utente A utilizza il proprio browser per aprire due connessioni con il server HTTP in esecuzione sull'host B. Come può il protocollo TCP distinguere queste due connessioni

- Risposta: Il socket in TCP è identificato dal IP sorgente e IP destinatario, oltre che ai due numeri di porta

## Esercizio 6

- $10^6$bit per secondo
- $10^3$ pacchetti al secondo
- Prodotto rate-ritardo = Mbps per RTT = quantità in bit possibili
- A questo punto divido i bit massimo possibile per la quantità di bit di un pacchetto, il risultato è il prodotto rate-ritardo

- 