___

Il livello di rete si occupa dell'instradamento dei datagrammi dal mittente al destinatario.

Il viaggio che esegue ogni datagramma passa per __switch__ e __router__, dove sale per lo stack protocollare fino al livello di rete e scende per continuare al prossimo.

Il __routing__ (Instradamento) determina il percorso seguito dai pacchetti dall'origine alla destinazione,
cioè attraverso quali router deve passare il pacchetto per raggiungere la destinazione.
È quello che costruisce i percorsi.

Il __forwarding__ (Inoltro) decide su quale porta di uscita deve imesso il pacchetto in base a quanto stabilito dal routing.

Ogni router possiede una tabella di routing
La tabella di routing specifica quale collegamento di uscita bisogna prendere per raggiungere la destinazione.

Uno __switch__ è un commutatore di pacchetti, si occupa del trasferimento dall'interfaccia di ingresso a quella di uscita.

Un __router__ esegue il forwarding in base al valore del campo del header del livello di rete, ovvero in base all'indirizzo IP.


# Switching

Si divide tra due approcci:
- Approccio a __circuito virtuale__, dove i due host e i nodi intermedi stabiliscono una connessione virtuale.
- Approccio a __datagramma__, dove ogni datagramma viaggia in modo indipendente dagli altri.

## Packet switching

I router della rete a datagramma non conservano informazioni sullo stato dei circuiti virtuali.

I pacchetti vengono inoltrati utilizzando l'indirizzo dell'host destinatario.

Il processo di inoltro funziona che:
- esistono dei prefissi all'interno del router, nel datagramma arrivato è presente un indirizzo IP di destinazione, a ogni range di prefissi è assegnato un interfaccia di uscita, e il router sceglie in base a quale range appartiene quel datagramma.

