___

## Come scrivere programmi paralleli

Tramite parallelizzazione dei task, cioè partizionare i compiti fra tutti i core. 

Tramite parallelizzazione dei dati, cioè partizionare i dati necessari per risolvere il problema fra tutti i core.

Ogni core computa operazioni simili sulla parte di dati assegnatoli.

I core hanno bisogno di coordinarsi tra di loro, per varie ragioni:
- Comunicazione tra core, dove si mandano dati tra di loro.
- Bilanciamento del carico di lavoro.
- Sincronizzazione delle operazioni da computare.

## Tipi di sistemi paralleli

Un sistema parallelo si suddivide in base alla gestione della memoria dei core:
- Memoria condivisa, dove ogni core accede alla memoria del computer e si coordinano esaminando e aggiornando questa memoria.
- Memoria distribuita, dove ogni core ha la sua memoria privata, e quindi devono mandarsi messaggi su un network per interagire/comunicare.

Un sistema parallelo si suddivide in base alla gestione della computazione dei core:
- Multiple istruzioni e multipli dati, dove ogni core ha la sua unità di controllo e quindi può computare in modo indipendente dagli altri core.
- Singola istruzione e multipli dati, dove ogni core condivide la stessa unità di controllo e quindi tutti i core devono eseguire la stessa istruzione allo stesso tempo, o stare fermi.

CUDA è SIMD e memoria condivisa.

MPI è MIMD e memoria distribuita.

OpenMP è MIMD e memoria condivisa.

CUDA può anche essere MIMD e memoria condivisa.

## Concorrente / Parallelo / Distribuito

Un sistema è:
- Concorrente quando multipli task possono essere in svolgimento in ogni tempo.
- Parallelo quando multipli task cooperano strettamente per risolvere un problema.
- Distribuito quando un programma potrebbe dover cooperare con altri programmi per risolvere un problema.

Sistemi paralleli e sistemi distribuiti sono anche concorrenti.

Sistemi concorrenti possono essere seriali.

Paralleli sono strettamente legati e distribuiti sono meno legati strettamente.

## von Neumann bottleneck

Il collo di bottiglia di von Neumann si riferisce alla separazione della CPU dalla memoria.

La CPU può leggere e scrivere dati nella memoria.

La velocità di trasmissione dei dati da memoria a CPU dipende dalla interconnessione (bus)

## Singolo programma multipli dati (SPMD)

Si compila un solo programma.

Questo programma viene eseguito da multipli processi.

Si usano i condizionali if-else per specificare cosa deve fare ogni processo.

I processi non condividono la memoria quindi per comunicare si fa passaggio di messaggi.

# MPI

MPI_Init: serve a dire a MPI di effettuare il setup necessario per MPI.

MPI_Finalize: serve a dire a MPI che il programma ha finito, e che quindi deve pulire tutte le allocazioni di memoria allocate per questo programma.

## Compilazione di programmi MPI

```C
mpicc -g -Wall -o executable_file source_file.c
```

-g serve per produrre tutte le informazioni di debug.
-Wall è warning all, quindi attiva tutti i possibili warning.
mpicc è il wrapper script usato per compilare.

## Esecuzione di programmi MPI

```C
mpiexec -n <numero di processi> <file_eseguibile>

mpiexec -n 4 ./file_eseguibile
```

### Debugging di programmi MPI

```C
mpiexec -n 4 ./file_eseguibile : -n 1 gdb ./file_eseguibile : -n 1 ./file_eseguibile
// Esegue il quinto processo in gdb e tutti gli altri 5 processi normalmente
```

___

Ogni processo di un programma in MPI viene identificato da un intero non negativo chiamato __rank__.

Un __comunicatore__ è una collezione di processi che possono mandare messaggi tra di loro.

MPI_Init definisce un comunicatore che consiste di tutti i processi creati quando il programma inizia.

Tale comunicatore è MPI_COMM_WORLD.

```C
int MPI_Comm_size( MPI_Comm comm, int* comm_sz_p);
// comm è il comunicatore da dare alla funzione per chiedere la sua grandezza
// comm_sz_p è l'output nella quale la funzione mette la grandezza del comunicatore
```

```C
int MPI_Comm_rank( MPI_Comm comm, int* my_rank_p);
// Questa funzione viene chiamata da un processo all'interno di un comunicatore per chiedere che rank ha all'interno di tale comunicatore.
```

```C
// Esempio di uso di MPI_Comm_size e MPI_Comm_rank

#include <stdio.h>
#include <mpi.h>

int main(void) {
	int comm_sz, my_rank;
	MPI_Init(NULL, NULL);
	MPI_Comm_size(MPI_COMM_WORLD, &comm_sz);
	MPI_Comm_rank(MPI_COMM_WORLD, &my_rank);
	printf("Hello from process %d out of %d\n", my_rank, comm_sz);
	MPI_Finalize();
	return 0;
}
```

___

MPI da la possibilità di creare nuovi comunicatori.

Due librerie MPI indipendenti possono comunicare tramite i tags oppure passandosi un comunicatore a ognuno delle due librerie. 

[[000 - Reworked notes#MPI part 2|continua qui sotto]]

___

## Come comunicano i processi MPI tra di loro

MPI_Send e MPI_Recv sono usati per mandare dati tra i processi.

```c
int MPI_Send( void* msg_buf_p, int msg_size, MPI_Datatype msg_type, int dest, int tag, MPI_Comm comm);
// msg_buf_p è il buffer dove è contenuto il dato da inviare
// msg_type è il tipo di dato del dato da inviare
// dest è il rank del processo alla quale mandare il dato
// tag è usato per differenziare i messaggi inviati da uno stesso processo (serve al destinatario)
```

```C
int MPI_Recv( void* msg_buf_p, int buf_size, MPI_Datatype buf_type, int source, int tag, MPI_Comm comm, MPI_Status* status_p);
// msg_buf_p è il buffer dove si mette il dato ricevuto
// msg_type è il tipo di dato del dato da ricevere
// source è il rank del processo dalla quale ricevere un dato
// tag è usato per differenziare i messaggi inviati da uno stesso processo
// status_p serve per dare informazioni su una comunicazione 
```

MPI richiede che i messaggi siano __non sorpassanti__, cioè che un processo che manda due messaggi a un altro processo, quest'ultimo deve poter ricevere il primo dei due messaggi prima dell'altro.

Non c'è una restrizione sull'arrivo di messaggi inviati da processi differenti.

Un messaggio viene ricevuto __correttamente__ se il tipo del dato ricevuto corrisponde a quello indicato durante la ricezione, e se la dimensione del buffer dove mettere il dato ricevuto è abbastanza grande.

Un processo può ricevere messaggi anche non sapendo la grandezza del dato ricevuto, oppure non sapendo chi lo manda, o anche non sapendo il tag del messaggio.

Per ricevere un dato della quale non si sa la grandezza, si usa MPI_Get_count.

```C
int MPI_Get_count( MPI_Status* status_p, MPI_Datatype type, int* count_p);
// Dare in input il tipo del dato e lo status del messaggio ricevuto
// La grandezza del messaggio ricevuto verrà inserito in count_p
```

Il problema con l'invio e ricezione di messaggi è che:
- MPI_Send potrebbe comportarsi in modo differente in base alla dimensione del buffer e altre variabili.
- MPI_Recv blocca sempre il processo che lo chiama finché non riceve un messaggio che corrisponde agli argomenti specificati.

Quindi l'esatto comportamento delle comunicazioni è determinato dall'implementazione in MPI.

# Parallel Program Design

## Metodologia di Foster

Partizionare la computazione da eseguire e i dati sulla quale la computazione opera in operazioni più piccole. (1)

L'obiettivo è identificare quali operazioni possono essere eseguite in parallelo. (1)

Serve determinare quali comunicazioni mandare per poter supportare il partizionamento in operazioni più piccole. (2)

Si deve combinare operazioni e comunicazioni che richiedono vincoli strettamente l'una con l'altra. (3)

Per esempio se un'operazione necessariamente deve essere eseguita dopo un'altra specifica operazione, allora è meglio combinarli in un unica operazione. (3)

Tale combinazione viene effettuata per minimizzare le comunicazioni, e in altri casi per avere che tutti i processi facciano la stessa quantità di lavoro. (4)

# Parallel Design Pattern

Possiamo distinguere i modelli di programmi paralleli in due categorie.

__Globalmente parallelo e localmente sequenziale__, GPLS, cioè che un'applicazione riesce a eseguire multiple operazioni in parallelo, dove ogni operazione viene eseguito sequenzialmente.

Modelli che rientrano in questa categoria includono:
- Singolo programma e multipli dati.
- Multipli programmi e multipli dati.
- Master-Worker.
- Map-Reduce.

__Globalmente sequenziale e localmente parallelo__, GSLP, cioè che un'applicazione viene eseguito come un programma sequenziale, dove certe parti individuali vengono eseguite in parallelo quando richiesto.

Modelli che rientrano in questa categoria includono:
- Fork/join.
- Loop parallelism.

___

## Singolo programma multipli dati (SPMD) (Modello di programma GPLS)

Singolo programma multipli dati (SPMD)

Si compila un solo programma.

Questo programma viene eseguito da multipli processi.

Si usano i condizionali if-else per specificare cosa deve fare ogni processo.

I processi non condividono la memoria quindi per comunicare si fa passaggio di messaggi.

Tutta la logica dell'applicazione viene mantenuta in un singolo programma.

Questo modello fallisce quando:
- I requisiti di memoria sono troppo alti per tutti i nodi.
- Piattaforme eterogenee sono coinvolte.

## Multipli programmi multipli dati (MPMD) (Modello di programma GPLS)

Multipli programmi e multipli dati (MPMD)

Gli step da eseguire per far funzionare un programma sono identici a SPMD.

Ma il deployment coinvolge diversi programmi.

___

MPI supporta sia SPMD che MPMD.

___

## Master-Worker (Modello di programma GPLS)

Il modello Master-Worker si basa su due componenti:
- Master.
- Workers.

Il master è responsabile della:
- Assegnamento di lavoro ai workers.
- Collezionare i risultati delle computazioni eseguite dai workers.
- Effettuare operazioni I/O per i workers.
- Interagire con l'utente.

Tale modello è buono per un bilanciamento implicito del carico di lavoro.

Ma il master può diventare un collo di bottiglia.

Risolto tramite l'uso di una gerarchia di master.

## Map-Reduce (Modello di programma GPLS)

Il modello Map-Reduce è una variante del Master-Worker.

Il Master-Worker esegue la stessa funzione su dati differenti.
Il Map-Reduce esegue la stessa funzione su diverse parti di un singolo dato.

## Fork/Join (Modello di programma LPGS)

Il modello Fork/Join si basa sull'esecuzione di un singolo thread.

Da tale thread si vanno a creare dinamicamente i suoi figli a tempo di esecuzione che svolgeranno le operazioni.

Queste operazioni possono essere eseguite tramite la creazione di thread figli, oppure assegnate ed eseguite da thread contenuti in un pool statico di thread.

Ogni thread figlio deve finire la sua esecuzione per far continuare il thread parente.

Questo modello di programma parallelo è quello usato da OpenMP e Pthreads.

## Loop parallelism (Modello di programma LPGS)

Il modello Loop parallelism viene utilizzato per eseguire la migrazione da codice software sequenziale o vecchio (legacy) a codice multicore (parallelo).

Tale modello si focalizza sullo spezzare i cicli (loops) tramite la manipolazione della variabile che controlla il loop.

Non tutti i loop sono supportati da questo modello.

Un loop deve essere in una forma particolare per supportare questa migrazione.

Quindi questo modello presenta una flessibilità limitata, ma è anche meno impegnativa da sviluppare.

Questo modello è supportato da OpenMP.

# MPI part 2

La maggiorparte delle implementazioni di MPI permettono solamente al processo con rank 0 all'interno di MPI_COMM_WORLD di poter accedere allo standard in (stdin).

Il processo 0 deve necessariamente leggere i dati (tipo scanf) e mandarli a tutti gli altri processi.

