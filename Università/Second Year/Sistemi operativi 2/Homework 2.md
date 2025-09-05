
Client-Server 

## Specifica client

L'applicazione client-server che permette a un client di inviare un dato cifrato a un server, e al server di decifrarlo.

L'applicazione riceve come input il nome di un file, una chiave K di lunghezza 64bit (unsigned long long int), l'indirizzo IP del server e il numero di porta su cui il server è in ascolto.

Il client legge il file e ne determina la lunghezza L. Lo divide in n blocchi Bi di lunghezza 64bit.
L'ultimo blocco potrebbe contenere meno di 64bit. In tal caso deve essere fatto il padding con '0' fino a riempire il blocco.

Per ogni blocco Bi il client calcola in bitwise XOR con K ottenendo quindi Ci=Bi XOR K.
Tale operazione deve essere eseguita in parallelo mediante p-thread con p<=n

Infine il client invia al server la sequenza di blocchi Ci nell'ordine corretto, la lunghezza L del file originale e la chiave K.

## Specifica server

Il server è in ascolto su di una specifica porta e accetta richieste di connessione da processi client.

