___

Explicit parallel programming in C language is done by using specific libraries and compilers.

In the course we have been exposed to $4$ different libraries:
1) __Message Passing Interface__, or MPI. (Library)
2) Posix threads, or Pthreads. (Library)
3) __OpenMP__. (Library and Compiler)
4) __CUDA__. (Library and Compiler)

Usiamo diverse librerie in base alle loro __proprietà__.

# Tipi di sistemi paralleli

Un sistema parallelo si suddivide in base alla gestione della memoria dei vari core:
- Memoria __condivisa__.
- Memoria __distribuita__.

Un sistema parallelo viene classificato anche in base alla gestione delle istruzioni date e delle unità di controllo:
- Multiple-Instruction Multiple-Data. (MIMD)
- Single-Instruction Multiple-Data. (SIMD)

|      | Shared Memory          | Distributed Memory |
| ---- | ---------------------- | ------------------ |
| SIMD | CUDA                   |                    |
| MIMD | Pthreads, OpenMP, CUDA | MPI                |

## Sistemi paralleli: A memoria condivisa

Nei sistemi paralleli a memoria condivisa:
- Ogni core ha accesso ad una singola memoria condivisa.
- I core si devono coordinare per evitare _race conditions, false sharing,..._
- Dato che condividono lo stesso spazio di memoria, questi sistemi offrono bassa latenza di comunicazione e usano meno memoria.
- La comunicazione avviene implicitamente.

## Sistemi paralleli: A memoria distribuita

Nei sistemi paralleli a memoria distribuita:
- Ogni core ha accesso ad una sua memoria privata.
- I core si devono coordinare tramite l'uso di __messaggi__ in una rete.
- La coordinazione quindi avviene esplicitamente.
- Data la distribuzione della memoria, questi sistemi hanno __scalabilità virtualmente infinita__.
- L'invio e ricezione di messaggi introduce un __overhead__.
- È comune anche un overhead di memoria, causata dalla duplicazione di dati spesso richiesti da diversi core.

## Sistemi paralleli: Con multiple unità di controllo (MIMD)

Nei sistemi paralleli con multiple unità di controllo:
- Ogni core possiede la sua propria unità di controllo.
- Quindi ogni core può eseguire istruzioni completamente differenti.
- Diversi rami di codice possono essere eseguiti allo stesso tempo.

## Sistemi paralleli: Con singola unità di controllo (SIMD)

Nei sistemi paralleli che usano una singola unità di controllo per multipli core:
- Tutti i core di una unità di controllo eseguono la stessa istruzione data, o restano inattivi. 
- Ciò può causare lo __stallo__ di alcuni core durante l'esecuzione di un ramo di codice, in quanto il sistema non può eseguire entrambi i rami simultaneamente.
- Il sistema quindi eseguirà tali rami in modo __sequenziale__, fermando prima un cammino e poi l'altro, finché non si ricongiungono.


> [!Note] Archittetura di von Neumann
> La CPU può leggere e scrivere dati nella memoria.
> 
> Il collo di bottiglia di von Neumann si riferisce alla separazione della CPU dalla memoria.
> 
> La velocità di trasmissione dei dati dalla memoria a CPU dipende dalla interconnessione usata.

# MPI

MPI è una libreria usata per parallelizzare programmi tramite l'invio e ricezione di messaggi basata sul modello di programmazione SPMD.

## MPI: Come iniziare e concludere MPI

All'interno di un programma, per usare MPI serve chiamare due funzioni:
- MPI_Init.
- MPI_Finalize.

Prima di chiamare MPI_Init non si può usare la libreria, e dopo aver chiamato MPI_Finalize stessa cosa.

### MPI_Init

Serve a effettuare il setup necessario per poter usare la libreria.

### MPI_Finalize

Serve ad annunciare che il programma ha concluso, richiedendo a MPI di pulire la memoria allocata per il programma.

## MPI: Identificare i processi MPI di un programma

I vari processi MPI di un programma sono identificati dai loro __rank__, un intero positivo.

## MPI: Comunicatori

Un comunicatore è un'insieme di processi MPI che possono mandarsi messaggi tra di loro.

La funzione MPI_Init quando eseguita, definisce un comunicatore che include tutti i processi MPI creati quando il programma inizia, chiamato MPI_COMM_WORLD.

### MPI: Comunicatori custom

MPI inoltre fornisce funzioni che servono a creare nuovi comunicatori, questi possono essere utili al programmatore per implementare funzionalità più complesse.

Supponendo di dover utilizzare $2$ librerie MPI indipendenti:
- Se si utilizza il comunicatore default (MPI_COMM_WORLD) i messaggi potrebbero collidere.
- Si potrebbero assegnare dei __tag__ (interi positivi) ai messaggi per distinguerli.
- Sarebbe meglio creare due nuovi comunicatori, uno per libreria.

### MPI_Comm_size

Serve a sapere il numero di processi MPI all'interno del comunicatore dato alla funzione come argomento.

### MPI_Comm_rank

Serve a sapere il rank del processo MPI chiamante all'interno del comunicatore dato alla funzione come argomento.

## MPI: Comunicazione tramite messaggi

La comunicazione tra i vari processi avviene tramite l'invio e ricezione di messaggi.

L'uso di messaggi comporta un overhead importante, quindi è consigliato inviare una sola volta più dati che inviare tante volte piccole porzioni di dati.

![](https://i.imgur.com/fj9ukDA.png)

### MPI_Send

Serve per inviare un messaggio.

```C
int MPI_Send( void* msg_buf_p, int msg_size, MPI_Datatype msg_type, int dest, int tag, MPI_Comm comm);
// msg_buf_p è il buffer dove è contenuto il dato da inviare
// msg_type è il tipo di dato del dato da inviare
// dest è il rank del processo alla quale mandare il dato
// tag è usato per differenziare i messaggi inviati da uno stesso processo (serve al destinatario)
```

### MPI_Recv

Serve per ricevere un messaggio.

```C
int MPI_Recv( void* msg_buf_p, int buf_size, MPI_Datatype buf_type, int source, int tag, MPI_Comm comm, MPI_Status* status_p);
// msg_buf_p è il buffer dove si mette il dato ricevuto
// msg_type è il tipo di dato del dato da ricevere
// source è il rank del processo dalla quale ricevere un dato
// tag è usato per differenziare i messaggi inviati da uno stesso processo
// status_p serve per dare informazioni su una comunicazione 
```

### MPI: Messaggi non sorpassanti

I messaggi tra due processi necessariamente devono essere __non sorpassanti__:
- Se un processo invia più messaggi allo stesso processo di destinazione, tali messaggi devono essere disponibili al destinatario nella stessa sequenza in cui sono stati inviati.
Mentre per i messaggi inviati da processi differenti non si applica tale regola.

### MPI: Ricezione corretta dei messaggi

Un messaggio viene ricevuto __correttamente__ se:
- Il tipo del dato scelto durante la ricezione corrisponde a quello indicato durante l'invio.
- E se la dimensione del buffer dove mettere il dato ricevuto è sufficiente.

Un processo può ricevere messaggi anche se:
- Non conosce la dimensione del dato ricevuto, tramite la funzione MPI_Get_count.
- Non conosce chi lo manda, tramite MPI_ANY_SOURCE.
- Non conosce il tag del messaggio, tramite MPI_ANY_TAG.

### MPI_Get_count

Serve per ottenere la dimensione del dato contenuto nel messaggio da ricevere.

```C
int MPI_Get_count( MPI_Status* status_p, MPI_Datatype type, int* count_p);
// Dare in input il tipo del dato e lo status del messaggio ricevuto
// La grandezza del messaggio ricevuto verrà inserito in count_p
```

### MPI: Problemi con l'invio e la ricezione di messaggi

Il comportamento esatto delle due funzioni è determinato dalla implementazione di MPI usata, quindi non si deve assumere niente sul loro comportamente fuori da ciò che viene definito dallo standard MPI, altrimenti il codice potrebbe essere poco portatile.

MPI_Send potrebbe comportarsi in modo diverso in base alla:
- Dimensione del buffer.
- Cutoffs.
- Blocking.

MPI_Recv blocca sempre l'esecuzione del processo che lo chiama finché non riceve un messaggio che corrisponde agli argomenti indicati alla chiamata.

## MPI: Tipi di comunicazione

Esistono vari tipi di comunicazione:
- Bufferata (Buffered).
- Sincrona (Synchronous).
- Ready.

### MPI: Tipo di comunicazione bufferata

Nella modalità di comunicazione bufferata, le operazioni di invio sono __sempre localmente bloccanti__, cioè sbloccano il processo chiamante non appena il messaggio inviato viene copiato in un buffer. Tale buffer è __fornito dall'utente__.

### MPI: Tipo di comunicazione sincrona

Nella modalità di comunicazione sincrona, le operazioni di invio bloccano il processo mittente.

Lo sblocco avviene solo dopo che il processo destinatario comincia l'operazione di ricezione del messaggio.

Tale operazione è una operazione __globalmente bloccante__, cioè il processo mittente __conosce lo stato__ del processo destinatario in quanto il mittente si sblocca quando il destinatario comincia la ricezione del messaggio. Non servono altri messaggi per confermare l'avvenuta ricezione.

### MPI: Tipo di comunicazione ready

Nella modalità di comunicazione ready, le operazioni di invio hanno successo solamente se un'operazione di ricezione __corrispondente__ è __già iniziata__, altrimenti l'invio restituisce un __codice di errore__.

Questa modailità serve a ridurre l'overhead delle operazioni di handshaking.

## MPI: Comunicazione non bloccante

Le operazioni di invio bufferate sono viste negativamente in quanto comportano un calo della performance, causato dal __blocco del processo chiamante__, che deve aspettare che il dato venga copiato nel buffer.

Quindi funzioni non bloccanti o immediate portano a __massimizzare la concorrenza__ in quanto:
- Sbloccano il processo chiamante immediatamente non appena viene inizializzato un trasferimento di dati.

In questo modo un processo può eseguire altre operazioni mentre il trasferimento viene effettuato.

Per questo sia MPI_Send che MPI_Recv hanno delle versioni non bloccanti e immediate.

Se i processi utilizzano le comunicazioni non bloccanti, questi necessariamente hanno bisogno di eseguire altre comunicazioni usate per conoscere lo stato di completamento della comunicazione iniziale:
- I processi mittente per poter modificare o riutilizzare il buffer del messaggio.
- I processi destinatario per poter cominciare ad estrarre il contenuto del messaggio.

Le comunicazioni non bloccanti possono essere unite con ogni tipo di comunicazione:
- MPI_Isend, MPI_Bsend, MPI_Ssend, ... (Immediate, Buffered, Synchronous)

### MPI: Controllare lo stato di completamento di una comunicazione

Esistono due funzioni principali per controllare lo stato di completamento di una comunicazione:
- MPI_Wait, bloccante.
- MPI_Test, non bloccante.

Altre varianti di queste due esistono, come:
- MPI_Waitall.
- MPI_Testall.
- MPI_Waitany.
- MPI_Testany.
- ...

#### MPI_Wait

Serve per bloccare un processo che ha un operazione di invio o ricezione in corso.

#### MPI_Test

Serve a controllare se una operazione di invio o ricezione è stata completata o meno.

## MPI: Comunicazioni collettive




# Progettazione (Design) di programmi paralleli (Metodologia di Foster)

La metodologia di Foster descrive i procedimenti da seguire per progettare programmi paralleli.

Fornisce un approccio per scomporre il problema da computare in modo da rendere l'esecuzione parallela efficiente.

Si divide in $4$ fasi:
- Partizionamento (Partitioning).
- Comunicazione (Communication), a seguito del partizionamento.
- Aggregazione (Agglomeration).
- Mappatura (Mapping)

Il partizionamento serve per dividere la computazione da eseguire e i dati su cui si opera in parti più piccole. L'obiettivo principale è identificare quali operazioni possono essere eseguiti in parallelo.

La comunicazione serve per determinare la comunicazione necessaria da usare per riuscire ad eseguire le operazioni definite durante il partizionamento.

L'aggregazione serve per combinare operazioni legate tra di loro in un'unica operazione più grande (Dipendenza). Per esempio se un'operazione A necessariamente viene prima di B, allora ha senso combinarli. (Per avere meno overhead)

La mappatura serve per assegnare le operazioni definite nei passi precedenti, in modo da minimizzare la comunicazione necessaria e assicurarsi che ogni processo o thread ottenga la stessa quantità di operazioni da eseguire.

# Modelli (Patterns) di progettazione parallela

I modelli di progettazione parallela servono ad organizzare i programmi paralleli, e si differenziano in base a come gestiscono il flusso dell'esecuzione del programma.

Tutti i modelli di progettazione parallela rientrano in $2$ categorie:
- Globally Parallel, Locally Sequential (GPLS).
- Globally Sequential, Locally Parallel (GSLP).

![](https://i.imgur.com/iray0k0.png)

## Modello di progettazione parallela: Globalmente parallelo e localmente sequenziale (GPLS)

I programmi che si basano su questo modello sono progettati per eseguire più operazioni contemporaneamente, con ogni singola operazione che esegue le proprie istruzioni in modo sequenziale.

Modelli che rientrano in questa categoria:
- Single-Program, Multiple-Data (SPMD).
- Multiple-Program, Multiple-Data (MPMD).
- Master-Worker.
- Map-Reduce.

### Single-Program Multiple-Data (SPMD)

Nel modello di programmazione SPMD, si compila un __singolo__ programma contenente __tutta la logica__ dell'applicazione che viene eseguito da multipli processi.

Tali processi vengono controllati tramite l'uso di blocchi _if-else_ e hanno bisogno di comunicare tramite l'invio e ricezione di messaggi in quanto non condividono la memoria.

Questo modello __fallisce__ quando:
- I requisiti di memoria sono troppo alti per ogni nodo.
- Oppure quando sono coinvolte piattaforme eterogenee. (?)

### Multiple-Program Multiple-Data (MPMD)

È simile a SPMD, ma esegue l'avvio di multipli programmi diversi che lavorano insieme.

### Master-Worker

In questo modello i processi si differenziano in Masters e Workers.

I Masters sono responsabili di:
- Distribuire parti di lavoro da far eseguire ai workers.
- Collezionare i risultati ottenuti dai workers.
- Eseguire operazioni di I/O per conto dei workers.
- Interagire con l'utente.

Il vantaggio di questo modello è che il carico di lavoro viene bilanciato __implicitamente__, anche se il processo Master può diventare un punto di __bottleneck__.

Tale collo di bottiglia è riducibile tramite l'uso di una __gerarchia__ di Masters.

### Map-Reduce

È una variante del modello Master-Worker.

I Masters gestiscono le operazioni da eseguire mentre i workers possono eseguono due tipi di operazioni:
- Map, cioè applicare una funzione a sezioni di un dato per generare risultati parziali.
- Reduce, cioè collezionare e combinare i risultati parziali per ottenere il risultato finale.

## Modello di progettazione parallela: Globalmente sequenziale e localmente parallelo (GSLP)

I programmi che si basano su questo modello sono progettati per eseguire un singolo processo inizialmente, e da questo si __generano altri processi__ per eseguire alcune parti in modo parallelo quando richiesto.

Modelli che rientrano in questa categoria:
- Fork/Join.
- Loop parallelism.

### Fork/Join

In questo modello l'esecuzione inizia con un singolo thread radice, per poi generare tramite __fork__ thread figli che vanno ad eseguire le operazione assegnate.

Il thread padre __non__ può continuare la sua esecuzione finché tutti i figli non finiscono le loro operazioni e ritornano al padre tramite __join__.

Questo è il modello usato da OpenMP e Pthread.

### Loop parallelism

Questo modello viene utilizzato per effettuare __migrazione__ di software __legacy__ o sequenziali.

Si concentra sullo scomporre i cicli tramite __manipolazione della variabile di controllo del ciclo__, in modo che thread diversi eseguano iterazioni del ciclo diverse.

Da notare però che __non__ tutti i cicli sono supportati, in quanto devono avere una forma molto specifica e __prevedibile__.

