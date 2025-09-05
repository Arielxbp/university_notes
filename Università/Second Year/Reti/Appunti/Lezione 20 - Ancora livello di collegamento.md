
## Indirizzi MAC

Quando un datagramma viene incapsulato in un frame al livello di collegamento, all'interno dell'intestazione del frame sono contenuti gli indirizzi di collegamento della sorgente e destinazione del frame, ovvero gli indirizzi di due nodi di un hop.

Gli indirizzi MAC sono composti da $48\space bit$.

Anche per gli indirizzi MAC esiste un indirizzo broadcast:
- FF-FF-FF-FF-FF-FF

Il campo per l'indirizzo MAC di destinazione è posto prima del campo per quello della sorgente perché in questo modo non vi è bisogno di utilizzare risorse per frame non destinati a loro.
Ciò è stato progettato proprio perché esistono gli indirizzi broadcast.

## Protocollo per la risoluzione degli indirizzi (ARP)

Ogni nodo nella LAN possiede una __tabella ARP__.

Queste tabelle servono per contenere la corrispondenza tra indirizzi IP e MAC.

In questo modo se si conosce anche solo l'indirizzo IP di un nodo è possibile determinare l'indirizzo MAC di destinazione.

Se un nodo deve inviare un datagramma a $x$ ma non presenta nella sua tabella ARP l'indirizzo MAC di $x$, allora manderà un pacchetto broadcasst contenente il messaggio di richiesta ARP, contenente l'indirizzo IP di $x$.

## Ethernet

