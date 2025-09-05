

Un attacco è definito come __intrusione__, ovvero un qualsiasi insieme di azioni che tenta di compromettere uno o più proprietà tra queste:
- L'integrità, cioè il contenuto della comunicazione non deve essere alterato.
- La confidenzialità, cioè che solo il mittente e il destinatario devono essere in grado di comprendere il contenuto del messaggio.
- La disponibilità, cioè che gli utenti legittimi devono poter usare i servizi di rete.

I programmi dolosi come virus e work possono introdursi all'interno degli host tramite vari metodi:
- Attachment
- Programmi scaricabili
- Sfruttando vulnerabilità di programmi già presenti negli host.

L'obiettivo di un attacco mira a creare un punto di appoggio per un futuro accesso tramite:
- Creazione di un account.
- Installazione di una __backdoor__.
oltre all'installazione di programmi dolosi e DDoS

## Port scanning

Usato per effettuare una scansione dettagliata dei singoli host per scoprire i servizi attivi.

## Tipi di attacchi

- Sniffing, ovvero spiare una comunicazione, capire che dati stanno venendo trasmessi.
- Spoofing, ovvero l'impersonare un altro soggetto.
- Hijacking, ovvero il dirottamento di una sessione in corso.
- DoS, ovvero mandare fuori uso alcuni servizi.

# Contromisure

## Antivirus

Sono software usati per rilevare ed eliminare programmi dolosi.

Esaminano i dati interni al host e rilevano la presenza di programmi dolosi noti.

Analizzano il comportamento dei programmi, in particolare le istruzioni __sospette__ eseguite da queste.

Deve essere costantemente aggiornato con la creazione di nuovi attacchi.

## Firewall

È una struttura sia hardware che software che separa una rete privata dal resto dell'Internet.

Consente all'amministratore di controllare e gestire il flusso del traffico dati, quindi solamente a quello autorizzato sarà consentito passare.

Il filtraggio dei pacchetti si basa sulla tabella ACL, ovvero una tabella di regole da applicare ai pacchetti entranti.

## IDS (Sistema di intrusion detection)

È un sistema passivo che si basa sull'analisi del traffico di rete.

Genera allarmi quando rileva azioni quali:
- Scansione delle porte o TCP/IP
- Attacchi DoS

Si basa su un packet sniffer usati insieme a un insieme di regole.

### Network based intrusion detection

Il sistema cattura e analizza il traffico di rete.

### Anomaly based intrusion detection

Il sistema crea un profilo di traffico "normale" e genera un allarme quando rileva un comportamento di rete anomalo.

Può avere elevati falsi positivi e falsi negativi ma può rilevare nuovi attacchi.

# Sicurezza della comunicazione

- Crittografia.
- Hash.
- Firma digitale.
