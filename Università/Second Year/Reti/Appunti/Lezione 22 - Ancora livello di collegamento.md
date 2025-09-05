
## CDMA (Code Division Multiple Access)

È un protocollo dove un solo canale occupa l'intera ampiezza di banda e dove tutte le stazioni possono inviare contemporaneamente pacchetti.

Un codice si dice __chip__.
A ogni stazione viene assegnato un codice che è una sequenza di numeri, che sono chip.

Per poter generare le sequenze di chip si usa una __tabella di Walsh__.
In questa tabella ogni riga è una sequenza di chip.

## Bluetooth

È una tecnologia LAN wireless progettata per connettere dispositivi con diverse funzioni.

Una LAN Bluetooth è una rete ad hoc, in quanto si forma senza la necessità di un AP.

Viene usata una banda da $2.4Ghz$ divisa in $79$ canali da $1Mhz$ ciascuno.

### Piconet

È una rete piccola composta al massimo da $8$ dispositivi, di cui $1$ stazione primaria e $7$ secondarie che si sintonizzano con la primaria.

### Scatternet

È una combinazione di Piconet.

Si viene a formare attraverso una stazione secondaria di una Piconet che funge da primaria per un'altra Piconet.

### Protocollo MAC: Bluetooth

La tecnologia Bluetooth usa TDMA.

## RFID (Radio Frequecy Identification)

All'interno di una rete RFID sono presenti:
- RF Tags, cioè degli oggetti che hanno un identificativo, un antenna integrata e un microchip.


I dispositivi RFID funzionano senza l'utilizzo di batterie.

I tag passivi, anche se privi di energia, funzionano quando vengono usati presso i reader in quanto riflettono il segnale proveniente dal reader e nel mentre modificandolo per funzionare.

### Identificazione dei Tag

Il canale tra il reader e i tag è broadcast.

Il reader quando invia un segnale:
- Se ritorna solo un segnale, ok.
- Se ritorna più di un segnale, il reader deve regolare l'accesso al canale.

### Protocolli MAC per RFID

Per i dispositivi RFI sono presenti:
- Protocolli basati su albero.
- Protocolli basati su ALOHA.

#### Frame Slotted ALOHA (FSA)

- Tempo in slots.

Reader esegue richiesta per un frame.
Ogni Tag sceglie uno slot di tempo di quel frame e inserisce all'interno dello slot scelto un numero randomico.

#### Tree Slotted ALOHA (TSA)

Ogni collisione genera un nuovo nodo dell'albero dove si riprova il trasferimento, se ancora collisione si continua, se no collisione allora si passa al prossimo slot.

