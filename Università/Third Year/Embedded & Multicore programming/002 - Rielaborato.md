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
> 

# Single-Program Multiple-Data (SPMD)

Nel modello di programmazione SPMD, si compila un __singolo__ programma che viene eseguito da multipli processi.

Tali processi vengono controllati tramite l'uso di blocchi _if-else_ e hanno bisogno di comunicare tramite l'invio e ricezione di messaggi in quanto non condividono la memoria.

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

MPI inoltre fornisce funzioni che servono a creare nuovi comunicatori, questi possono essere utili al programmatore per implementare funzionalità più complesse.

### MPI_Comm_size

Serve a sapere il numero di processi MPI all'interno del comunicatore dato alla funzione come argomento.

### MPI_Comm_rank

Serve a sapere il rank del processo MPI chiamante all'interno del comunicatore dato alla funzione come argomento.

## MPI: Comunicazione tramite messaggi

La comunicazione tra i vari processi avviene tramite l'invio e ricezione di messaggi.

L'uso di messaggi comporta un overhead importante, quindi è consigliato inviare una sola volta più dati che inviare tante volte piccole porzioni di dati.

### MPI_Send

```C
int MPI_Send( void* msg_buf_p, int msg_size, MPI_Datatype msg_type, int dest, int tag, MPI_Comm comm);
// msg_buf_p è il buffer dove è contenuto il dato da inviare
// msg_type è il tipo di dato del dato da inviare
// dest è il rank del processo alla quale mandare il dato
// tag è usato per differenziare i messaggi inviati da uno stesso processo (serve al destinatario)
```

### MPI_Recv

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

