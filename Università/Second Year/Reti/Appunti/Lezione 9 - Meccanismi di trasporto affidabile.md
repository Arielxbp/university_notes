___

# Stop and wait (meccanismo)

- È un meccanismo per controllare l'esito del trasporto di un pacchetto
- In questo meccanismo il mittente invia un pacchetto alla volta e aspetta l'acknowledgement dal destinatario prima di spedire i successivo pacchetto
- L'acknowledgement viene inviato dal destinatario dopo che esso calcola il checksum sul pacchetto ricevuto
- Il mittente usa anche un timer per capire se il pacchetto inviato è stato perso, ovvero non riceve indietro l'acknowledgement
- Il meccanismo utilizza dei numeri di sequenza per identificare ogni pacchetto e per gestire diversi casi possibili:
	1) Mittente invia pacchetto x -> Pacchetto arriva correttamente -> Destinatario invia 'ack' -> Mittente riceve 'ack' -> Mittente invia pacchetto x+1
	2) Mittente invia pacchetto x -> Pacchetto è corrotto o non arriva al destinatario -> Scade il timer -> Mittente reinvia il pacchetto x
	3) Mittente invia pacchetto x -> Pacchetto arriva corretamente -> Destinatario invia 'ack' -> 'ack' viene perso o corrotto -> Scade il timer -> Mittente reinvia il pacchetto x	
- Per i numeri di sequenza bastano i numeri binari 0 e 1
- Si usano i numeri di riscontro per indicare il numero di sequenza del prossimo pacchetto atteso dal destinatario
- Non è un meccanismo efficiente

# Go back N (protocollo)

- Utilizza il meccanismo del pipelining, cioè il mittente ammette più pacchetti in transito
- Utilizza ack cumulativi, cioè l'acknowledgement ora indica che tutti i pacchetti fino al numero di sequenza sono stati ricevuti correttamente
- Il mittente possiede un timer per il più vecchio pacchetto non riscontrato (non ackato), e alla scadenza il mittente reinvia tutti i pacchetti dal più vecchio pacchetto non riscontrato fino all'ultimo inviato
- Serve avere la dimensione della finestra di invio minore dei numeri di sequenza
- Se si perde un pacchetto, si deve per forza rispedire tutto quanto, quindi non è ancora molto efficiente

# Ripetizione selettiva

- In Go back N per un solo pacchetto perso si ritrasmettono tutti i successivi già inviati nel pipeline. Questo peggiora la congestione della rete
- Nella ripetizione selettiva il mittente rispedisce solamente i pacchetti per i quali non ha ricevuto un acknowledgement
- Il destinatario invia riscontri specifici per i pacchetti ricevuti correttamente, che possono essere ordinati e non
- Le finestre di ricezione e invio hanno la stessa dimensione
- La ripetizione selettiva usa un timer per ogni pacchetto in attesa di riscontro, quindi quando scade il timer verrà inviato solamente il pacchetto collegato a tale timer
- È computazionalmente più costoso

# Esercizio 1

- Usando numeri di sequenza a 5 bit, qual'è la dimensione massima delle finestre di invio e di ricezione per per ciascuno dei meccanismi seguenti?
- Per lo Stop-and-Wait: $1$ e $1$
- Per Go back N: $2^{5}-1=31$ e $1$
- Per Selective repeat: $2^{5-1}=16$ e $2^{5-1}$

# Esercizio 2

- Send first: 0
- Send next: 4
- Result next: 2
- m: 3
- finestra di invio: 7
1) 2, 3
2) 1, 2