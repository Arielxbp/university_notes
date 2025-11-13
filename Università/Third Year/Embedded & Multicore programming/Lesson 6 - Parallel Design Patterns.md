___

I pattern sono usati per parallelizzare applicazioni.

## GPLS (Globally Parallel, Locally Sequential)

I processi sono tutti eseguiti in parallelo, ma ogni processo esegue le sue instruzioni iinterne in modo sequenziale.

Alcuni pattern che implementano questa metodologia:
- Single-Program Multiple Data
- Multiple-Program Multiple Data
- Master-Worker
- Map-reduce

### Single-Program Multiple Data

Questo pattern è usato da OpenMPI.

### Multiple-Program Multiple Data

Esistono più programmi che 

### Master-Worker

Il processo Master distribuisce il lavoro ai Worker.

I worker eseguono il lavoro e restituiscono il risultato al Master.

Il __load balancing__ viene effettuato automaticamente in quanto i worker veloci otteranno più lavoro da svolgere.

Il bottleneck è il processo Master.

### Map-Reduce

È una variazione del (Master-Worker)


## GSLP (Globally Sequential, Locally Parallel)

È un unico processo sequenziale, ma che può creare altri processi per eseguire alcune istruzioni in modo parallelo.
F
Alcuni pattern che implementano questa metodologia:
- Fork/Join
- Loop parallelism


#  User input in OpenMPI

Solo il processo $0$ può leggere dallo __stdin__ (dipende dall'implementazione di OpenMPI).

Quindi il processo $0$ deve leggere i dati proveniente dallo __scanf__ per poterli mandare agli altri processi.

L'invio deve essere fatto singolarmente per ogni processo.
```c
if (my_rank == 0){
	scanf(...);
	for (dest; dest < comm_sz; dest++){
		MPI_Send(...)
		...
		MPI_Send(...)
	}
}
```

Notare che non è possibile mandare un puntatore a una struttura dati contenente tutti i dati letti dallo scanf in quanto tale puntatore punta a un'indirizzo di memoria presente solo nello spazio di memoria del processo $0$.

Quindi come alternativa si usano delle funzioni che effettuano in una singola call queste multiple send per esempio.

# Collective Communication

È possibile definire delle funzioni custom che definiscono come operare in modi particolari su dati. (MPI_OP_Create)

## MPI_Reduce

```c
int MPI_Reduce(
	void* input_data_p // Elemento di partenza
	void* output_data_p // Elemento in uscita specificato dalla radice
	int count
	MPI_Datatype datatype // Tipo dell'elemento
	MPI_Op operator // Operazione da eseguire
	int dest_process // Processo destinazione
	MPI_Comm comm // Comunicatore sulla quale i processi scambiano messaggi
)
```

Tutti i processi all'interno del comunicatore __necessariamente__ devono chiamare la stessa funzione collettiva.
Si nota che se un processo all'interno del comunicatore __non__ esegue la chiamata della funzione, l'operazione finisce in __deadlock__ per tutti i processi del comunicatore.


Le funzioni collettive non presentano un tag.

Quando si effettuano più chiamate a una stessa funzione collettiva, queste non si influenzano e se gli altri processi chiamano una sola volta la funzione collettiva, questa andrà a buon fine perchè e vanno a matchare con la prima funzione colletiva chiamata.

