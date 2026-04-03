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

## MPI: Input al programma

La maggiorparte delle implementazioni di MPI permette solamente al processo $0$ del comunicatore MPI_COMM_WORLD di accedere allo _stdin_.

Quindi il processo $0$ necessariamente deve leggere i dati e mandarli agli altri processi.

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

## MPI: Comunicazione tra più processi contemporaneamente

Quando due o più processi hanno bisogno di scambiarsi dati a vicenda, questi hanno bisogno di effettuare ognuno un'invio e una ricezione, e l'__ordine__ con cui le due operazioni vengono effettuate è importante:
- Se entrambi effettuano una ricezione, allora andranno a bloccare la loro esecuzione in attesa di un messaggio, finendo in __deadlock__.
- Se entrambi effettuano un'invio, è possibile comunque finire in __deadlock__ se la dimensione del dato inviato è grande.

Per evitare queste situazioni, è consigliato usare la funzione MPI_Sendrecv.

### MPI_Sendrecv

Serve per inviare e ricevere simultaneamente un messaggio.

```C
int MPI_Sendrecv(void* send_buf_p, int send_buf_size, MPI_Datatype send_buf_type, int dest, int send_tag,
				 void* recv_buf_p, int recv_buf_size, MPI_Datatype recv_buf_type, int source, int recv_tag,
				 MPI_Comm communicator, MPI_Status* status_p);
```

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

Le comunicazioni collettive sono operazioni che coordinano il __trasferimento__ o la sicronizzazione di dati tra un __insieme di processi__ all'interno di uno specifico comunicatore.

Per poter avviare una funzione collettiva, __tutti__ i processi all'interno di uno specifico comunicatore devono chiamare la __stessa__ funzione collettiva.

Siccome queste funzioni sono collettive, non richiedono come argomento un __tag__.

Il risultato della funzione collettiva può essere usato solamente dal processo indicato come destinatario della collettiva. Tutti gli altri processi inseriranno _NULL_ come argomento del buffer di output.

Inoltre, gli argomenti passati in input da ogni processo alla funzione collettiva devono essere __compatibili__.

Per esempio:
- Un processo passa in input come destinazione della collettiva il processo con rank $0$ e un altro processo passa il processo con rank $1$, allora la funzione MPI_Reduce va in errore e il programma molto probabilmente crasha o si blocca.

### MPI_Reduce

È una funzione di __riduzione__ di dati basata sull'__operatore MPI__ dato come argomento.

```C
int MPI_Reduce( void* input_data_p, void* output_data_p, int count, MPI_Datatype datatype, MPI_Op operator, int dest_process, MPI_Comm comm);

// Esempio di uso
MPI_Reduce(&local_int, &total_int, 1, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);
```

![|500](https://i.imgur.com/G4e8bqA.png)

### MPI_Bcast

È una funzione di __broadcasting__ che invia a tutti i processi all'interno del comunicatore di appartenenza i dati indicati dal processo chiamante.

```C
int MPI_Bcast(void* data_p, int count, MPI_Datatype datatype, int source_proc, MPI_Comm comm);

// data_p è sia input che output
```

### MPI_Allreduce

È una combinazione di due funzioni collettive:
- MPI_Reduce e MPI_Bcast.

Cioè viene eseguito prima la riduzione, seguito da un broadcast del risultato ottenuto dalla riduzione.

```C
int MPI_Allreduce(void* input_data_p, void* output_data_p, int count, MPI_Datatytpe datatype, MPI_Op operator, MPI_Comm comm)
```

### MPI_Scatter

Serve per __distribuire__ un vettore che viene letto dal processo con rank $0$ a tutti gli altri processi, tale operazione manda a ognun processo solamente la __partizione__ sulla quale deve operare.

```C
int MPI_Scatter(void* send_buf_p, int send_count, MPI_Datatype send_type, void* recv_buf_p, int recv_count, MPI_Datatype recv_type, int src_proc, MPI_Comm comm);

// send_count indica il numero di elementi da mandare a ogni processo
// e non indica il numero totale di elementi del vettore

// recv_buf_p = MPI_IN_PLACE -> la partizione assegnata al processo
// chiamante non viene copiata e poi reincollata in un altro buffer
// ma rimane nel buffer iniziale
```

Per mandare numeri differenti di elementi a ogni processo esiste la variante MPI_Scatterv.

### MPI_Gather

Serve per __raccogliere tutte__ le partizioni del vettore presenti nei vari processi, e inviare il tutto nel buffer del processo con rank $0$.

```C
int MPI_Gather(void* send_buf_p, int send_count, MPI_Datatype send_type, void*, recv_buf_p, int recv_count, MPI_Datatype recv_type, int dest_proc, MPI_Comm comm);

// send_count indica il numero di elementi da mandare a ogni processo
// e non indica il numero totale di elementi del vettore
```

### MPI_Allgather

È una combinazione di due funzioni:
- MPI_Gather e MPI_Bcast.

Cioè viene eseguito prima la raccolta dei dati, seguito da un broadcast del vettore ottenuto dalla raccolta.

```C
int MPI_Allgather(void* send_buf_p, int send_count, MPI_Datatype send_type, void* recv_buf_p, int recv_count, MPI_Datatype recv_type, MPI_Comm comm);

// send_count e recv_count indicano il numero di elementi mandati da ogni processo
```

### MPI_Alltoall

Serve ad inviare una partizione del proprio vettore a tutti gli altri processi che chiamano la funzione.

![](https://i.imgur.com/M3hxpbd.png)

## MPI: Rilevanza degli algoritmi delle funzioni collettive

Data l'importanza delle funzioni collettive, e il loro maggiore impatto sul tempo di esecuzione totale del programma rispetto alle altre operazioni, queste hanno bisogno di essere ottimizzate per poter decidere quale algoritmo usare in base alla situazione attuale, quanti processi sono involti, ...

Per questa ragione esistono varie implementazioni di librerie di funzioni collettive.

## MPI: Tipi di dato derivati

In MPI, **derived datatypes** allow developers to create custom communication structures for complex data that goes beyond basic, predefined types (like standard integers or floats). They solve the problem of needing to send or receive collections of mixed or non-contiguous data items (such as a C `struct`) over the network without requiring manual buffer management.

Here is a breakdown of how they work and why they are useful:

- **Mapping Memory Layout:** A derived datatype is formally defined by specifying a **sequence of basic MPI data types along with their specific memory displacements** (their relative locations or offsets in memory).
- **Automatic Packing on Send:** Instead of forcing the programmer to write manual code to pack different variables into a single, contiguous buffer before sending, you can simply pass the derived datatype to your send function. Because the send function understands the types and exact memory locations of all the items, **it automatically collects the scattered items directly from memory** and packages them for transmission.
- **Automatic Unpacking on Receive:** Similarly, when the destination process receives the message, the receive function uses the derived datatype to **automatically distribute the incoming data items directly into their correct, corresponding memory locations**.

**How They Are Created** MPI provides several specialized functions to build these custom datatypes depending on how your data is laid out:

- **`MPI_Type_create_struct`**: Builds a derived datatype consisting of individual elements that have different basic types (perfect for standard C `structs`).
- **`MPI_Type_contiguous`**: Builds a datatype for a series of contiguous elements.
- **`MPI_Type_vector`**: Builds a datatype for elements of the same type that are repeated and separated by a regular interval or "stride".
- **`MPI_Type_create_subarray`**: Used to select and communicate multidimensional subarrays.

When creating these types—especially structs—it is highly recommended to use `MPI_Get_address` to find the exact memory displacements of the items. This ensures the derived datatype correctly accounts for any invisible memory padding the compiler might introduce, which can vary between 32-bit and 64-bit platforms. Once the datatype is built, you must call **`MPI_Type_commit`** to allow the MPI library to optimize its internal representation before you can use it in a communication function.

## MPI: Valutazione della performance (Profiling)

Durante lo sviluppo del programma parallelo, è possibile controllare il periodo di tempo trascorso tra due punti del codice.

### MPI_Wtime

Serve ad ottenere il numero di secondi trascorsi da qualche tempo prima.

```C
double MPI_Wtime(void);

// Esempio d'uso
start = MPI_Wtime();
...
finish = MPI_Wtime();
printf("Elapsed time = %e seconds\n", finish-start);
```

## MPI: Threading

I processi MPI possono usare __threads__ per velocizzare ancora di più un programma.

Per poter usare threads, bisogna chiamare MPI_Init_thread al posto di MPI_Init, indicando necessariamente il livello di threading richiesto e il livello di threading supportato dal sistema.

### MPI: Livello di threading

In MPI esistono $4$ livelli di threading:
1) MPI_THREAD_SINGLE.
	- Nessun rank può usare threads.
2) MPI_THREAD_FUNNELED.
	- Ogni rank può usare threads, ma solo il __thread principale__ può chiamare funzioni MPI.
	- Ideale per parallelizzazione __fork/join__ come in **`#pragma omp parallel`** dove tutte le chiamate MPI sono fuori dai blocchi OpenMP.
3) MPI_THREAD_SERIALIZED.
	- Ogni rank può usare threads, ma solamente un thread alla volta può chiamare funzioni MPI.
	- Un thread deve quindi assicurarsi di essere l'unico al momento a chiamare una funzione MPI, realizzabile tramite l'uso di __mutex__.
4) MPI_THREAD_MULTIPLE.
	- Ogni rank può usare threads, e non ci sono limitazioni.
	- La libreria MPI deve assicurarsi che gli accessi ai dati sono sicuri per tutti i threads.

# Valutazione della performance

## Rumore (Noise during runs)

Per ridurre il rumore che va ad influire sui dati ottenuti durante le misurazioni, è possibile usare delle __barriere__, che se poste all'inizio del programma, vanno ad assicurare più o meno che tutti i processi inizino allo stesso tempo.

Per questo:
- Più il numero di processi/threads/GPUs aumenta, più è possibile che almeno uno di questi venga influenzato dal rumore.

## Proporzione numero di processi : dimensione del problema

Generalmente:
- Il tempo di esecuzione aumenta all'aumentare della dimensione del problema.
- Il tempo di esecuzione diminuisce all'aumentare del numero di processi.

Esiste però un __limite__ alla riduzione del tempo di esecuzione all'aumentare del numero di processi:
- Se il numero di processi $X$ è abbastanza grande da computare il problema.
- Usando $Y\gg X$ processi è possibile che non si abbia abbastanza lavoro da suddividere per tutti i processi, in tal caso alcuni processi resterebbero inutilizzati, non portando quindi a __nessuna riduzione del tempo di esecuzione__.

## Riduzione del tempo di esecuzione (Speedup)

Idealmente, quando si esegue un programma con $X$ processi, questo dovrebbe essere $X$ volte più veloce rispetto a quando lo si esegue con $1$ processo.

Dato il tempo seriale $T_{s}(n)$ e il tempo parallelo usando $X$ processi $T_{p}(n,X)$, l'__aumento di velocità__ di esecuzione del programma calcolato usando $$S(n, X)=\frac{T_{s}(n)}{T_{p}(n, X)}$$ idealmente dovrebbe essere uguale a $X$, risultando in un __aumento lineare__.

Inoltre, il tempo parallelo usando $1$ processo, generalmente dovrebbe essere più o veloce uguale __rispetto al tempo sequenziale__.

## Scalabilità del programma parallelo (Scalability)

Dato il tempo parallelo usando $1$ processo $T_{p}(n, 1)$ e il tempo parallelo usando $X$ processi $T_{p}(n, X)$, la __scalabilità__, ovvero quanto il programma parallelo riesce ad utilizzare al meglio più processi per velocizzare la computazione, viene calcolato usando $$S(n, X)=\frac{T_{p}(n, 1)}{T_{p}(n, p)}$$

## Efficienza (Efficiency)

Idealmente l'efficienza di un programma parallelo dovrebbe essere uguale ad $1$.

Se tale valore è minore di $1$, allora il programma __performerà peggio__ all'aumentare della dimensione del problema.

L'efficienza viene calcolata usando $$E(n, X)=\frac{T_{s}(n)}{X\times T_{p}(n, X)}$$

## Strong Scaling e Weak Scaling

Lo __strong scaling__ è calcolabile:
- Fissando la dimensione del problema, si va ad aumentare il numero di processi.
- E se l'efficienza rimane alta, allora il programma parallelo è __strong scalable__.

Il __weak scaling__ è calcolabile:
- Aumentando la dimensione del problema allo __stesso ritmo__ con cui si aumenta il numero di processi.
- Quindi se si aumenta di un fattore $2$ la dimensione del problema, si aumenta di un fattore $2$ il numero di processi.
- E se l'efficienza rimane alta, allora il programma parallelo è __weak scalable__.

## Legge di Amdahl

Ogni programma ha delle parti che sono __impossibili da parallelizzare__:
- Leggere e scrivere sul disco, mandare e ricevere dati dalla rete, ...

La legge di Amdahl enuncia che lo __speedup__ è __limitato__ dalla frazione seriale (__serial fraction__), cioè $$T_{p}(X)=(1-\alpha)\times T_{s}+\alpha\times \frac{T_{s}}{X}$$
dove $1-\alpha$ è la parte di codice eseguibile solo sequenzialmente.

### Legge di Amdahl: Limitazioni

La frazione seriale potrebbe aumentare quando aumentano il numero di __processori__. (?)

## Legge di Gustafson

Se si considera il __weak scaling__, la frazione parallela (__parallel fraction__) aumenta all'aumentare della dimensione del problema.

Ciò è anche noto come __scaled speedup__, ovvero $$S(n, X)=(1-\alpha)+\alpha\times X$$

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

# OpenMP (Open MultiProcessing)

OpenMP è una libreria usata per parallelizzare programmi in sistemi a memoria condivisa, e tali programmi seguono il modello Globally-Sequential Locally-Parallel (GSLP), in particolare tramite __fork/join__.

Tale sistema è visto come un'insieme di core o CPU, le quali hanno tutti accesso ad una memoria principale __condivisa__.

OpenMP si affida a delle __direttive del compilatore__ per segnalare i blocchi di codice che il compilatore proverà a parallelizzare.

## OpenMP: Gestire il numero di thread da usare

Esistono $3$ livelli di controllo del numero di thread da usare all'interno di un processo:
- __Universale__, definendo il numero di threads tramite una __variabile d'ambiente__.
- Livello del __programma__, definendo il numero di threads chiamando la funzione **`omp_set_num_threads`** al di fuori dai blocchi di codice segnati dalle direttive OpenMP.
- Livello del __pragma__, definendo il numero di thread nella stessa riga della direttiva pragma OpenMP usando la clausola **`num_threads`**.

La __precedenza__ viene data prima al numero di thread indicato più specificatamente, ovvero:
- __Più importante__: livello del pragma.
- __In mezzo__: livello del programma.
- __Meno importante__: Universale.

### OpenMP: Team

In OpenMP, l'insieme del thread originale più i nuovi threads generati che eseguono un blocco di codice parallelo viene definito come __team__.

(Similmente ai comunicatori in MPI)

### OpenMP: omp_get_num_threads (funzione)

Serve ad ottenere il numero di threads attivi in un blocco di codice parallelo.

Se la funzione viene chiamata in una regione sequenziale, restituisce $1$.

### OpenMP: omp_get_thread_num (funzione)

Serve ad ottenere il rank (id) del thread chiamante.

## OpenMP: Pragmas

OpenMP si affida come detto alle delle direttive del compilatore, in particolare usa **`#pragma`** per indicare al compilatore dei comportamenti specifici.

## OpenMP: pragma omp parallel (direttiva)

È la direttiva di parallelizzazione più semplice.

Il numero di threads che eseguono il blocco di codice delimitato viene __determinato dal sistema a tempo di esecuzione__.

```C
# pragma omp parallel num_threads(thread_count)
{
	function();
}

// int my_rank = omp_get_thread_num(); // Rank del thread chiamante
// int thread_count = omp_get_num_threads(); // Numero totale di threads
```

Dopo l'esecuzione di un blocco di codice parallelo, una __barriera implicita__ bloccherà i vari thread.

### OpenMP: pragma omp end parallel (direttiva)

Serve per indicare la fine di un blocco di codice parallelo.

## OpenMP: sezioni critiche tramite clausola critical (clausola)

Serve per indicare un __blocco di codice__ che può essere eseguito da un solo thread alla volta.

```C
# pragma omp critical
{
	global_result += my_result;
}
```

### OpenMP: sezioni critiche denominate

OpenMP fornisce l'opzione di __aggiungere un nome__ alle direttive **`critical`**.

È possibile eseguire direttive **`critical`** con __nomi diversi simultaneamente__, quindi più di un thread alla volta può eseguire lo stesso blocco di codice critico.

Per poter fare ciò, serve definire queste direttive a __tempo di compilazione__.

```C
# pragma omp critical(name)
{
	// critical section
}
```

## OpenMP: Locks

OpenMP fornisce una sua implementazione delle chiavi (locks).

```C
omp_lock_t writelock; // dichiarazione 
omp_init_lock(&writelock); // inizializzazione

# pragma omp parallel for
{
	for (i = 0; i < x; i++) {
		...
		omp_set_lock(&writelock); // ottieni la chiave
		... // Codice eseguibile solo da un thread alla volta
		omp_unset_lock(&writelock); // restituisci la chiave
		...
	}
}
```

## OpenMP: pragma omp atomic (clausola)

Serve per indicare che un'__operazione sulla memoria__ deve essere effettuata in modo __atomico__, ovvero senza interferenze da altri thread.

La clausola **`atomic`** è più __efficiente__ e __veloce__ di **`critical`** in quanto deve proteggere solamente un'operazione invece che un blocco di operazioni.

La variabile viene protetta in lettura, scrittura e modifica, ma la parte destra dell'operazione viene __comunque eseguito in parallelo__.

```C
# pragma omp atomic
	global_result += function();

// global_result è protetto
// function() viene comunque eseguito da tutti i thread 
```

## OpenMP: Cosa usare tra sezioni critiche, operazioni atomiche e locks

Generalmente le direttive atomiche in teoria sono il metodo più veloce per ottenere la __mutua esclusione__, tuttavia in base all'implementazione OpenMP scelta:
- Le direttive atomiche potrebbero applicare la mutua esclusione attraverso __tutte__ le direttive atomiche __presenti nell'intero programma__.
- Quindi anche operazioni atomiche che __non__ si influenzano minimamente potrebbero essere mutualmente escluse.
- (Tutto ciò varia in base all'implementazione scelta di OpenMP)

L'uso delle chiavi (locks) invece è consigliato da usare per situazioni dove serve la mutua esclusione per una __struttura dati__ piuttosto che per un blocco di codice.

È __pericoloso__ annidare (nest) costrutti usati per implementare la mutua esclusione.

Infine, è __sconsigliato__ e anche __pericoloso__ mischiare costrutti differenti per implementare la mutua esclusione, in quanto non c'è una __garanzia__ su chi viene eseguito prima (__fairness__).

## OpenMP: pragma omp parallel reduction (clausola)

In OpenMP, una riduzione serve a computare un dato, ottenuto applicando lo stesso operatore di riduzione ad una sequenza di operandi.

__Tutti i risultati intermedi__ ottenuti applicando l'operatore durante l'operazione di riduzione sono salvati in una stessa variabile.

Un'operatore di riduzione è un'operazione binaria:
- Addizione o sottrazione **`+, -`**.
- Moltiplicazione o potenza **`*, ^`**.
- And o Or **`&&, ||`**.
- Bitwise And o Or **`&, |`**.

Ogni thread al suo interno ha una copia privata della variabile indicata dalla clausola **`reduction( operatore : variable)`**, e tale variabile viene inizializzata al __valore d'identità__ dell'operatore usato.

Alla fine del blocco di codice parallelo, avviene la riduzione, che va ad accumulare i valori computati all'interno del blocco insieme al valore presente fuori dal blocco.

```C
int var;
# pragma omp parallel num_threads(thread_count) reduction(* : global_result)
{
	var += function(); // Qui global_result è inizializzato a 1 (valore d'identità per moltiplicazioni)
}

// var = var * var_di_thread_1 * ... * var_di_thread_thread_count
```

## OpenMP: Scope delle variabili

In OpenMP, per scope di una variabile si intende l'insieme dei threads che possono accedere a tale variabile all'interno di un blocco di codice parallelo.

Una variabile che può essere acceduta da tutti i thread di un team:
- Ha scope __condivisa__ (shared).

Una variabile che può essere acceduta solamente da un singolo thread:
- Ha scope __privata__ (private).

Di default ogni variabile __dichiarata al di fuori__ di un qualsiasi blocco OpenMP:
- Ha scope condivisa.

## OpenMP: Specificare lo scope delle variabili all'interno di un blocco (clausola)

È possibile usare la clausola **`default`** per manualmente specificare lo scope di ogni variabile che viene usata in un blocco di codice parallelo.

Lo scope predefinito delle variabili __dichiarate al di fuori__ dei blocchi di codice parallelo è **`shared`**.

La clausola **`shared`** bisogna esplicitamente indicarla quando **`default(none)`** viene specificato.

### OpenMP: private (clausola)

La clausola **`private`** se indicata, va a creare __una copia separata__ di una variabile __per ogni__ thread nel team. Queste copie __non__ sono inizializzate, quindi all'interno del blocco di codice parallelo __non hanno un valore assegnato__.

```C
int shared_var = 10;
# pragma omp parallel default(none) shared(shared_var) private(private_var)
{
	int private_var = 1; // Serve inizializzare private_var
	private_var += shared_var;
}
```

### OpenMP: firstprivate (clausola)

La clausola **`firstprivate`** è una versione della clausola **`private`** più avanzata, in quanto la variabile indicata dalla clausola viene __automaticamente inizializzata__ all'interno di ogni thread del team con il valore che ha la stessa variabile ma fuori dal blocco di codice parallelo.

```C
int private_var = 1;
# pragma omp parallel firstprivate(private_var)
{
	// Non serve inizializzare private_var
	private_var += 10; // 1 + 10
}
```

### OpenMP: lastprivate (clausola)

La clausola **`lastprivate`** è una versione della clausola **`private`** più avanzata, in quanto la variabile indicata dalla clausola viene __automaticamente trasferita fuori__ alla fine della computazione del blocco di codice parallelo dall'ultimo thread che lo esegue.

Inoltre è possibile usare **`firstprivate`** e **`lastprivate`** insieme.

```C
int private_var = 1;
# pragma omp parallel firstprivate(private_var) lastprivate(private_var)
{
	private_var += 10; // 1 + 10
}
printf(private_var); // 11
```

### OpenMP: threadprivate e copyin (clausole)

**Persistent Global Variables (`threadprivate` and `copyin`)** Sometimes, a thread needs a private variable that doesn't just disappear when a single parallel loop ends, but rather lives on to be used in future parallel regions.

- **`threadprivate`**: This directive is used to make **global or static variables** private to each thread. Unlike standard private variables, **the value of a `threadprivate` variable is preserved and persists across multiple different parallel regions** throughout the entire execution of the program. This allows each thread to maintain its own independent state or memory across distinct phases of your computation.
- **`copyin`**: Because `threadprivate` variables are persistent across the whole program, they do not get automatically initialized when a new parallel region begins. If you want all threads to start a new parallel region with the same baseline value for a `threadprivate` variable, you use the `copyin` clause. It **takes the value currently held by the master thread and copies it into the `threadprivate` variables of all the other threads in the team**.

## OpenMP: pragma omp parallel for (direttiva)

Serve a far eseguire un ciclo **`for`** da un team di threads.

Il blocco di codice segnato da questa direttiva necessariamente __deve essere__ un ciclo **`for`**.

La parallelizzazione del ciclo viene eseguito tramite l'__assegnamento delle iterazioni__ del ciclo tra i vari threads.

Inoltre OpenMP impone la dichiarazione del ciclo in un modo specifico, in quanto serve al sistema per determinare il numero di iterazioni a tempo di esecuzione. 

![](https://i.imgur.com/CltEq3J.png)

### OpenMP: limitazioni sulla forma della dichiarazione del ciclo

La variabile **`index`** deve essere di tipo **`integer`** o puntatore a **`integer`**, o sue versioni più grandi come **`long`**.

Le espressioni **`start`**, **`end`** e **`incr`** devono essere compatibili con **`index`**.

Le espressioni **`start`**, **`end`** e **`incr`** __non__ devono cambiare durante l'esecuzione del ciclo.

Durante l'esecuzione del ciclo, la variabile **`index`** può solamente essere modificata dall'espressione **`incr`** definito nella dichiarazione del ciclo.

__Non__ è possibile inserire **`break`** o **`return`** all'interno del ciclo.

### OpenMP: cicli for annidati e come collassarli tramite clausola collapse (clausola)

Se ci sono cicli **`for`** annidati, spesso è sufficiente parallelizzare solamente il ciclo __più esterno__.

Quando però il ciclo più esterno ha poche iterazioni in proporzione al numero di threads utilizzati, e si prova allora ad parallelizzare il ciclo interno, è possibile che l'efficienza rimanga comunque bassa.

![](https://i.imgur.com/Znu4IsQ.png)

La soluzione è far __collassare__ il tutto in un __singolo ciclo__, ciò si può fare manualmente:

![](https://i.imgur.com/ZsMTF8L.png)

o farlo fare ad OpenMP tramite la clausola **`collapse`**:

![](https://i.imgur.com/Umt6ofM.png)

