___

# Indirizzamento IPv4

L'indirizzo IP non dipende dalla macchina ma dalla rete.

Anche se una macchina si collega tramite due metodi, avrà 2 indirizzi IP diversi, in quanto ogni __interfaccia__ di host ha un indirizzo IP diverso.

Un router deve avere almeno due indirizzi IP.

L'indirizzo IP è composto da $32\space bit$, suddivisi tra il __prefisso__ e il __suffisso__, alle quali sono divise in modo dinamico i bit dell'indirizzo IP.

Il prefisso individua la rete mentre il suffisso serve ad individuare il collegamento con un host.

## Notazione CIDR

La struttura dell'indirizzo IP:
- Parte di rete
- Parte per l'host
- Un numero che indica il numero di bit nella parte di rete

## Maschera

La maschera è un numero composto da $32\space bit$ in cui i primi $n$ bit a sinistra sono impostati a $1$ e il resto ($32-n$) a $0$.

# DHCP (Protocollo)

Consente all'host di ottenere dinamicamente il suo indirizzo IP dal server di rete.


1) Il client manda una richiesta DHCP.

# Forwarding (Inoltrare)

Inoltrare il datagramma al prossimo hop (router)

