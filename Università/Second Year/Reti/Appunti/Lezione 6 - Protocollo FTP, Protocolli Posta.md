___

- Siamo ancora nel livello applicazione

# File Transfer Protocol (FTP)

- È un protocollo che permette di trasferire e ricevere file da una macchina remota
- Sono un insieme di comandi eseguibili da terminale
- La connessione che si stabilisce tra le due macchine è di tipo TCP
- La trasmissione dei dati passa attraverso una connessione diversa da quella di controllo
- La connessione di controllo è definita "fuori banda" (out of band) in quanto non viaggia sulla stessa connessione di quella per i dati
- Il protocollo presenta dei codici di stato che indicano lo stato della connessione

# Posta elettronica

- User agent: programma usato per mandare la mail
- Il messaggio da inviare viene passato prima al MTA
- MTA: Message Transfer Agent
- MAA: Message Access Agent
## Protocollo SMTP

- Gestisce il movimento della mail tra l'user agent e il suo server di posta
- Gestisce il movimento della mail tra i server di posta
- Usa connessioni TCP per trasferire i messaggi
- Richiede che i messaggi inviati siano nel formato ASCII a 7 bit

## Protocollo MIME

- Usato per convertire dati non nel formato ASCII a 7 bit per poter inviare tali dati nei messaggi


## Protocollo POP3 (Post Office Protocol)

- È più semplice del protocollo IMAP
- La connessione che si effettua usando il protocollo POP3 verso il server di posta è di tipo TCP
- Una volta stabilita la connessione si procede in 3 fasi:
	1) Autorizzazione: l'agente utente invia dati utente per l'identificazione
	2) Transazzione: L'agente utente recupera i messaggi dal server di posta
	3) Aggiornamento: Dopo aver ricevuto i messaggi dall'agente utente, il server cancella i messaggi marcati per la rimozione

## Protocollo HTTP (per le mail)

- L'agente utente in questo caso è il browser
- L'agente utente comunica con il server mediante il protocollo HTTP ma il trasferimento tra i server di posta usa comunque il protocollo SMTP