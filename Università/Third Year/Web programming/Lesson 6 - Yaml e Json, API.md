___

Entrambi sono "linguaggi" per manipolare dati.

# Json

È un formato leggero usato per trasmettere dati sulla rete.

Viene utilizzato anche per archiviare dati e configurare impostazioni.

La sintassi presenta solamente due tipi di dati:
- Un nome.
- Un dizionario (python)

# Yaml

È un linguaggio usato per serializzare dati.

Viene utilizzato anche:
- Come linguaggio all'interno di file di configurazione.
- Per archiviare dati.
- Per scambiare dati.

Il formato d testo è basato sull'indentazione tabulare, quindi senza l'uso di `;`.

Le stringhe in Yaml possono essere scritte senza `""`.

Gli elementi in un array in Yaml sono divisi da un `-` e sono uno per riga.

I file Json possono essere validi file Yaml, ma non il contrario.


# API (Application Programming Interface)

Un'API è un set di interazioni possibili tra un servizio e il client.

Essa definisce:
- Le richieste possibili.
- I parametri delle richieste effettuabili.
- I valori di ritorno delle chiamate.
- Qualsiasi formato di dato richiesto come Yaml, XML, Json.

L'adozione di un'API è vantaggiosa per l'architettura di un software in quanto porta a:
- Un interfaccia esplicita, che definisce precisamente le modalità di interazione.
- Un contratto infrangibile, ovvero stabilisce un insieme di regole che entrambi i lati rispettano.
- Information Hiding, in quanto la logica e il codice interno del provider rimangono nascoste al client.

## API private

Queste sono destinate all'uso interno di un'azienda o un sistema chiuso.
In questo modo l'accesso a tali funzionalità è limitato ai componenti interni.

## API pubbliche

Queste sono disponibili per l'uso da parte del pubblico. Tali funzionalità sono generalmente limitate tramite un numero massimo di accessi, ricordate tramite __API tokens__.

## Documentazione e definizione

La definizione di un'API deve essere esplicita, ovvero deve essere documentata tramite documentazione apposita.

Oppure si può usare un linguaggio di descrizione standardizzato, che formalizza il contratto, andando così a generare automaticamente la documentazione.

# OpenAPI

OAS (OpenAPI Specification) è il linguaggio di descrizione principale per le API basate su HTTP.

I file OpenAPI sono scritti in formato YAML per la loro leggibilità.


## Hi Lo game

Il gioco:
- avviare(), crea una nuova partita, l'oracolo sceglie il suo numero per la durata della partita ed inizializza il contatore di scommesse a 10
- scommettere(), il client propone un numero, l'oracolo aggiorna il contatore, l'oracolo restituisce vinto/perso/high/low
- abbandona()
- resettare()