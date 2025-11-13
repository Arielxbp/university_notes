___

## MPI_Bcast (Broadcast)

```c
int MPI_Bcast(
	void* data_p // Vettore di elementi da inviare/ricevere 
	int count //
	MPI_Datatype datatype // Tipo di dato degli elementi trasmessi
	int source_proc //
	MPI_Comm comm //
)
```

Il `data_p` per il processo $0$ è considerato come un input, cioè cosa si vuole inviare a tutti gli altri processi.
Gli altri processi lo considerano invece come output, in quanto ricevono dal processo $0$.

```c
// Nel processo 0
// si vuole trasmettere dato_x
// agli altri processi
MPI_Bcast(dato_x, 1, MPI_Datatype, 0, MPI_COMM_WORLD);

// Negli altri processi
// il dato_x inviato dal processo 0
// si troverà nel dato_y
MPI_Bcast(dato_y, 1, MPI_Datatype, 0, MPI_COMM_WORLD);
```

## MPI_Allreduce

È la combinazione di due funzioni:
- MPI_Reduce.
- MPI_Bcast.
Prima viene eseguito la riduzione dei dati, per poi usare una broadcast per inviare il risultato a tutti gli altri processi.

```c
int MPI_Allreduce(
	void* input_data_p
	void* output_data_p
	int count
	MPI_Datatype datatype
	MPI_Op operator
	MPI_Comm comm
)
```

___

## Scalability

Strong scalable: fissato la dimensione del problema, se aumentando il numero di processi si riesce a mantenere una efficienza alta, allora è strong scalable.

Weak scalable: all'aumento della dimensione del problema, si aumenta dello stesso moltiplicatore il numero di processi, e se si riesce a mantenere una efficienza alta, allora è weak scalable.

