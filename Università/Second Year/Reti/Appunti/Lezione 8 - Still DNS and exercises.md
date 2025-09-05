___

# Esempio Università

- L'università ospita:
	- Un web server per il sito istituzionale (www.uniroma1.it)
	- Un mail server per la gestione della posta elettronica (mail.uniroma1.it)
	- Un server DNS di autorità per il dominio uniroma1.it
- Ogni server è una macchina distinta con il proprio IP
- Il server DNS dell'università contiene le informazioni sugli altri 2 server dell'università
- I server DNS di autorità contengono record A, MX, CNAME, ...

# Esercizio 1

- Domanda: Si vuole aggiungere un nuovo protocollo nel livello applicazione, quali modifiche è necessario apportare agli altri livelli?
- Risposta: Nessuna modifica deve essere apportata agli altri livelli, basta che il protocollo al livello applicazione sia compatibile con i servizi del livello trasporto

# Esercizio 2

- Domanda: Quando si dice che il livello di trasporto effettua il multiplexing e il demultiplexing dei messaggi a livello applicazione, si intende che il protocollo di livello applicazione può combinare più messaggi del livello applicazione in un pacchetto?
- Risposta:No, perché non si può combinare più messaggi in un solo pacchetto, solo un messaggio per pacchetto.

# Esercizio 3

- Domanda: Perché nel contesto client/server il server deve essere permanentemente in esecuzione mentre il client può essere eseguito solo quando necessario
- Risposta: Perché il server deve essere pronto ad accettare le richieste dai client, mentre il client deve essere acceso solo quando è necessario

# Esercizio 4

- Domanda: Un client FTP deve prelevare due file dal server e depositavi un altro file. Quante connessioni di controllo e quante connessioni di trasferimento dati sono necessarie?
- Risposta: Il protocollo FTP permette di eseguire una sola connessione di controllo ma la connessione di trasferimento dati viene riservata per un singolo file, quindi si avranno 3 connessioni dati e 1 di controllo.

# Esercizio 5

- Domanda: È possibile per un server FTP ottenere l'elenco dei file o directory dal client?
- Risposta: No, il server non può inviare richieste al client.

# Esercizio 6

- Domanda: Quali tipi di RR sono memorizzati in un server DNS root?
- Risposta: Solo RR type A e RR type NS

# Esercizio 7

- Domanda: Un file contiene 2 milioni di byte
- (1) Quanto si impiega a trasmettere il file usando un canale a 56kbps?
- (2) E usando un canale a 1Mbps?
- Risposta:
- (1) $2.000.000*8 / 56000=285.7142857143$s
- (2) 16.000.000/10^\6 = 16s

# Esercizio 8

- Domanda: Si consideri un host A che vuole inviare un file molto grande e un host B. Il percorso tra A e B ha 3 link, con bitrate1=500kbps, bitrate2=2Mbps, bitrate3=1Mbps
- (1) Qual'è il throughput per il file trasfer?
- (2) Supponendo che il file sia grande 4 milioni di byte. Dividendo la grandezza del file per il throughput, quanto impiegherebbe all'incirca per trasferire il file all'host B
- (3) Ripetere le domande con bitrate2=100kbps
- Risposta:
- (1) Il throughput è dato dal bitrate1 in quanto è il bottleneck tra i 3 bitrate, quindi 500kbps
- (2) 32.000.000 bits / 500 * 10^\3 b

# Esercizio 9

- server client links

# Esercizio 10

- Domanda: Si vuole inviare un file di 160000 bits dall'host A all'host B su una rete a commutazione di circuito. I link hanno rate pari a 1536 kbps e usano il TDM con 48slot/sec. Il tempo per stabilire il circuito tra A e B è 500ms. Quanto inpiega l'host A a trasmettere il file?
- Risposta: 1536 * 10^\3/48 = 32000 bps
- 160000/32000 = 5s+500ms

# Esercizio 11

- Domanda: 
- Risposta: HTTP
- GET
- quotation7.htm
- no
- si

# Esercizio 12(1)

- Domanda: 