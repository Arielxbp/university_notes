___

The function `MPI_Send` can be globally blocking or locally blocking.

There are three communication modes:
- __Buffered__, in this mode the sending operation is __always__ locally blocking.
- __Synchronous__, in this mode the sending operation will return only when the destination process has initiated and started the retrieval of the message. This is a __globally blocking__ operation.
- __Ready__, in this mode the sending operation will fail if the receive operation has not been initiated already. This mode is used to reduce overhead of handshaking operations.
ÈÈÈ\\\\\\
These operations can be called respectedly using:
- `MPI_Bsend`
- `MPI_Ssend`
- `MPI_Rsend`

# Non-blocking Communication

Generally buffered sends are considered bad from a performance standpoint, because the caller has to block, waiting for the copy to take place.

Meanwhile non-blocking or __immediate__ functions, maximize __concurrency__ by returning instantly upon initiating a transfer.

The downside is that the completion of the operations for both end-points, has to be queried explicitly:
- The sender could be re-using or modifying the message buffer.
- The receiver could be extracting the message contents.
So non-blocking communications when needed should use a `wait()` function, because maybe MPI didn't copy fully the message.

Also non-blocking communications can be coupled with any communication mode:
- `MPI_Ibsend`
- `MPI_Issend`
- `MPI_Irsend`

## Non-blocking Send

```c
int MPI_Isend(void *buf,
			  int count,
			  MPI_Datatype datatype,
			  int dest,
			  int tag,
			  MPI_Comm comm,
			  MPI_Request *req // Handle for checking the status
			 )
```

## Wait (Blocking check)

```c
int MPI_Wait(MPI_Request *req,
			 MPI_Status *st
			)
```

Esistono le varianti `Waitall()` e `Waitany()`.

## Non-blocking check

```c
int MPI_Test(MPI_Request *req,
			 int *flag, // This value is set to true if operation is complete
			 MPI_Statuus *st // This will hold the comm. information
)
```

Esistono le varianti `Testall()` e `Testany()`.

