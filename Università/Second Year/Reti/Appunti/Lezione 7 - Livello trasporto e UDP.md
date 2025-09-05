___

# Indirizzamento dei processi

- L'indirizzamento a livello trasporto è dato dal numero di porta
- Serve poter individuare gli host e i processi tra i due host:
	- Per individuare gli host: Host -> indirizzo IP
	- Per individuare i processi: Processo -> numero di porta

# Socket

- L'indirizzo IP insieme al numero di porta costituiscono il socket address
- È necessario una coppia di indirizzi socket, uno locale e uno remoto
- L'indirizzo socket locale viene fornito dal sistema operativo
- L'indirizzo socket remoto, che contiene il numero di porta e l'indirizzo IP, sono rispettivamente noti in base all'applicazione e forniti dal DNS.
- Dal punto di vista del server, l'indirizzo socket remoto, ovvero quello del client, si trova all'interno del pacchetto di richiesta
## Numeri di porta

- È un indirizzo da 16 bit
- I primi 1023 numeri di porta sono fissi, prestabiliti per precisi processi



# Multiplexing/Demultiplexing

- a


# Servizio di TCP

- È orientato alla connessione, vi è uno scambio di messaggi che pone il client e l'host 
- Il trasporto fra i processi d'invio e di ricezione è affidabile
- È possibile controllare il flusso di informazioni mandate al destinatario in modo da non farlo sovraccaricare
- È possibile controllare la congestione, cioè limitare il processo d'invio quando la rete è sovraccaricata

# Servizio di UDP (non affidabile)

- È un protocollo "senza connessione", cioè non è richiesto alcun setup fra i processi client e server
- Non offre un servizio affidabile perché non è possibile controllare la rete come con il TCP
- Esiste perché è veloce

# UDP (User Datagram Protocol)

- È un protocollo di trasporto inaffidabile ed è privo di connessione
- Il mittente invia pacchetti in modo libero in quanto non viene limitato da alcun controllo (di flusso, di congestione)
- Ogni pacchetto è indipendente dagli altri pacchetti
- La sequenza dei pacchetti può arrivare in modo disordinato
- I datagrammi UDP hanno una dimensione limitata, quindi i processi devono passare solamente messaggi di dimensioni inferiori a 65507 byte, in quanto dal totale dei 65535 byte del datagramma, 8 vengono usati per l'intestazione UDP e 20 vengono usati per l'intestazione IP.

DNS usa UDP perché DNS è un protocollo molto semplice, dove non deve mandare grandi pezzi di pacchetti, non importa se un messaggio di risposta si perde.

#

- 