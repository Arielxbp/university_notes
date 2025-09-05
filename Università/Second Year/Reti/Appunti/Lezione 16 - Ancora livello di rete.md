___

Il __routing__ ha il compito di trovare il miglior percorso per i pacchetti, e lo inserisce nella tabella di routing.
Quindi il routing costruisce le tabelle mentre il forwarding le usa.

# Routing intra-dominio

## Algoritmo di instradamento con vettore distanza

Ogni nodo riceve informazioni dai nodi vicini e opera su quelle.

## Protocollo RIP (Protocollo di routing)

È un protocollo a vettore distanza.
Il costo è misurato in distanze, dove la massima distanza sono 15 hop, mentre 16 hop indica il valore infinito.

Si utilizza all'interno di reti piccole, dove il numero di salti è minore di 15.

È implementato attraverso processi client/server, quindi si presentano i messaggi RIP
- RIP Request, quando un nuovo router viene inserito nella rete, questa invia una RIP Request per ricevere informazioni di routing.
- RIP Response, è il messaggio di risposta a una request

Vengono usati dei timer per i messaggi:
- Timer periodico, che controlla l'invio dei messaggi di aggiornamenti.
- Timer di scadenza, che gestisce la validità dei percorsi ogni 180s, e durante questo periodo, se non si riceve un aggiornamento, allora il percorso viene considerato scaduto e il suo costo viene impostato a 16, ovvero infinito.
- Timer per garbage collection, che elimina i percorsi dalla tabella ogni 120s, cioè quando le informazioni non sono più valide, il router continua ad annunciare il percorso con costo di 16, e quando scadono i 120s, il router rimuove tale percorso.

È implementato come applicazione con UDP sulla porta 250.




# Routing inter-dominio