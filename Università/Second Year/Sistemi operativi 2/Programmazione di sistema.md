___

La programmazione di sistema interagisce direttamente con il __kernel__.

Per comunicare con il kernel si utilizzano le __system call__.

Si usano le system call rispetto alle librerie in quanto tramite l'eliminazione di un layer (libreria), si va a velocizzare le prestazioni.

> [!NOTE] System call nel man
> Le system call si trovano all'interno del man alla pagina 2

Le funzioni di libreria general purpose __non__ sono punti di accesso ai servizi del kernel, ma possono invocare system call perché implementate in quel modo.

## Differenza tra system call e funzioni general purpose

Entrambe sono funzioni C ed entrambe forniscono servizi ad un'applicazione.

Una funzione general purpose può essere rimpiazzata ma una system call no.

Le funzioni di libreria semplificano l'uso delle system call.

# System call

Sono divise in categorie:
- File
- Gestione della memoria
- Processi

## Errori (errno)

Le system call che terminano con un errore:
- restituiscono il valore $-1$.
- Impostano la variabile globale "errno" con il codice specifico dell'errore che si è generato durante l'esecuzione.
mentre quelle che terminano correttamente lasciano la variabile "errno" invariata.

Solitamente dopo aver verificato la presenza di una system call errata, è necessario assegnare il valore "errno" a una nuova variabile immediatamente all'interno del corpo dell'if:
```c
if (systemcall() == -1) {
	int err = errno;
	// gestione errore
	...
}
```

## Allocazione della memoria

Le funzioni per l'allocazione della memoria:
- malloc
- calloc
- realloc
restituiscono un __puntatore__ (void \*).

Serve quindi fare il __casting__ al tipo di puntatore relativo al tipo di dato contenuto nella memoria per poter utilizzare correttamente il puntatore.
(cioè in base al tipo di dato si avranno celle di dimensioni diverse)

Sempre eseguire la funzione "free(pointer_to_allocated)" dopo aver finito di usarlo.
### Realloc
```C
void *realloc(void *ptr, size_t size)
```

Modifica la dimensione dell'area di memoria precedentemente allocata con malloc/calloc e puntata da "ptr" nella dimensione specificata dal valore di "size"

## System call: Files

Un file è un astrazione che può essere ogni risorsa.

Le azioni che si possono eseguire su un file sono:
- Apertura mediante __open__.
- Operazioni su file mediante syscall __write__ o __read__.
- Chiusura del file mediante __close__.

I file descriptor

### open()
```C
int open(const char *path, int flags)
int open(const char *path, int flags, mode_t mode)
```

È una system call che restituisce un file descriptor.

- Il parametro "flags" indica se si vuole leggere, eseguire, appendere o una combinazione di queste.
- Il parametro "mode" indica le modalità di creazione del file.

A differenza con il fopen() la open() non restituisce un puntatore a un oggetto di tipo FILE.

### read()
```C
ssize_t read(int fd, void *buf, size_t count)
```

- Il parametro "fd" è un file descriptor.
- Il parametro "buf" è un puntatore a un area di memoria in cui memorizzare i byte letti.
- Il parametro "count" è il numero di byte da leggere.

La differenza tra read() e fread():
- read() non è bufferizzata.
- read() lavora sui byte indipendentemente dal tipo di dato in essi contenuto.
- fread() legge da uno stream di tipo FILE, la quale è bufferizzata.

### write()
```C
ssize_t write(int fd, const void *buf, size_t count)
```

- Il parametro "fd" è un file descriptor.
- Il parametro "buf" è l'area di memoria da cui leggere i dati, ed è dichiarata const per non essere modificata dalla funzione.
- Il parametro "count" è il numero di byte da scrivere.

### close()
```C
int close(int fd)
```

- Il parametro "fd" è un file descriptor.

Chiude il file descriptor "fd". (Viene liberato e può essere riutilizzato)

Nel caso venga chiuso l'ultimo file descriptor che fa riferimento a un file rimosso, allora il file viene cancellato.

### dup()
```C
int dup(int oldfd)
```

Questa syscall __duplica__ il file descriptor "oldfd" e restituisce il valore del nuovo file descriptor.

Se si scrive tramite il file descriptor nuovo, i cambi si rispecchiano anche nel file descriptor vecchio.(?)

### stat()
```C
int stat(const char *path, struct stat *buf)
```

Restituisce in "buf" le informazioni di stato del file specificato con nome file "path".


### fcntl()
```c
int fcntl(int fd, int cmd, ...);
```

È una syscall che permette di effettuare operazioni sul file descriptor fd come:
- Duplicazione del fd.
- Manipolazione del flag file descriptor.
- Manipolazione del flag di stato.

È possibile tramite questa syscall eseguire dei __lock__ su file:
- F_SETLK, per acquisire/rilasciare un lock.
- F_SETLKW, per acquisire/rilasciare un lock bloccante.
- F_GETLK, per testare l'esistenza di una lock.
Tutti questi sono numeri che possono essere stabiliti all'interno della struttura (struct) flock, che verrà dato in input alla syscall al posto dei ...

### select()

È una syscall che permette di monitorare uno o più file descriptor rimanendo in attesa che almeno uno di essi sia disponibile per effettuare l'operazione richiesta.

L'uso di questa syscall permette di sincronizzare dei processi tramite il monitoraggio della disponibilità dell'accesso a un file.

Vengono messe disponibili $4$ macro per la gestione degli insieme dei file descriptor:
- FD_ZERO(), per svuotare un insieme.
- FD_SET(), per aggiungere un file descriptor a un insieme.
- FD_CLR(), per rimuovere (clear) un file descriptor da un insieme.
- FD_ISSET(), per testare se un file descriptor appartiene a un insieme.

## System call su directories

```C
DIR *opendir(const char *name)
struct dirent *readdir(DIR *dirp)
int closedir(DIR *dirp)
```

Queste $3$ non sono system call ma funzioni di libreria.
Permettono di aprire una directory il cui stream è restituito da "opendir".

La funzione "readdir" legge il contenuto della directory, una profondità alla volta (come il strtok), sempre se esiste un prossimo elemento disponibile, e ritorna la struttura "dirent" o NULL se non ci sono più elementi.

## Creazione di processi

Il processo __init__ è il processo $0$, ed è il processo padre di tutti i processi del sistema in esecuzione.

Ogni processo fa rifermento al processo padre:
- Quando nasce eredita codice e parte dello stato dal processo padre.
- Quando muore/termina ritorna l'exit status al processo padre.
Se il processo padre muore/termina prima del processo figlio, allora quest'ultimo verrà adottato dal init.

## Processo zombie

È uno stato in cui può trovarsi un processo.

Un processo è nello stato zombie quando è stato terminato, ma che ha ancora il suo PCB mantenuto nella tabella dei processi dal kernel per dare modo al processo padre di leggere l'exit status del processo figlio.

## fork()

Crea un nuovo processo che è la copia del processo chiamante.

```c
pid = fork();
if (pid==0) {
	ChildProcess();
} else {
	ParentProcess();
}
```

Il processo eredita:
- I real ed effective usere group ID
- groups ID
- working directory
- ambiente del processo
- descrittori dei file
- terminale di controllo
- memoria condivisa, nel senso che li eredita, non che condividono la stessa zona di memoria

## abort()

Invia un segnale SIGABRT per il processo chiamante.
Il processo se chiama abort() verrà terminato in modo anormale, tale segnale comunque può essere intercettata e gestita.

## wait()

È un segnale che viene usato per far attendere un processo padre rispetto al figlio. Cioè si usa per attendere cambiamenti di stato in un figlio del processo chiamante, e quindi per ottenere informazioni sul figlio il cui stato è cambiato.

Il segnale permette al sistema di rilasciare le risorse associate al figlio che è terminato. Quindi se non viene eseguito il segnale di attesa wait(), allora il figlio terminato rimane in uno stato zombie.

## execve()

Solo execve() è system call, mentre le altre sono funzioni di libreria.

Servono per rimpiazzare un processo figlio con un altro processo.

Quando viene usato il execve() per cambiare un processo, non vengono preservati:
- Effective UID
- Effective GID
- Memory mapping
- Timers
- Memoria condivisa
- Memory lock


# Ambiente di un processo

È costituito da una serie di stringhe della forma key=value.
Definito tramite un array di puntatori a char, terminato da NULL.

Per default, l'ambiente di un processo coincide con l'ambiente del processo padre. (Da fork())


no bueno eseguire comandi di shell dall'interno del codice

# Segnali

Sono __interrupt__ software, inviati dal kernel a un processo o da un processo a un altro.

Quando si verificano condizioni anomale vengono generate INTERRUPTS.

Possono essere generate anche da condizioni __non__ anomale.

Gli unici segnali che __non__ possono essere ignorati sono:
- SIGKILL
- SIGSTOP
inoltre tali segnali non possono essere catturati.

Per gestire un segnale che viene generato serve usare un __handler__.
I handler interrompono il flusso di esecuzione del processo per eseguire l'handler associato al segnale per poi riprendere l'esecuzione dal punto in cui era stato interrotto.

## signal()

Serve per impostare l'handler del segnale inserito come parametro.
Restituisce SIG_ERR o il valore del precedente handler.


# Inter Process Communication

Unix mette a disposizione $2$ tipi di IPC:
- FIFO
- pipe


# Socket

Consentono la comunicazione tra processi nel paradigma client-server. (anche tra diversi host)

Le syscall associate a queste operazioni per comunicare sono:
- socket(), serve per creare la struttura dati della socket.
- bind(), serve per associare un nome alla socket.
- listen(), serve per mettere un processo in ascolto su una socket.
- accept()

## socket()
```c
int socket(int domain, int type, int protocol);
```

AF_UNIX (Stessa macchina)
AF_INET (famiglia di indirizzi IPv4)
AF_INET6 (famiglia di indirizzi IPv6)

## bind()
```c
int bind(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
```

Il sockfd è l'id di un socket unnamed.
Il addr è una struttura di tipo sockaddr che contiene l'indirizzo IP/nome della socket.
- struct socaddr_in per AF_INET o AF_INET6
- strcut socaddr_un per AF_LOCAL
Il valore addrlen è la dimensione della struttura sockaddr

## listen()
```c
int listen(int sockfd, int backlog);
```


## accept()
```c
int sockfd, struct sockaddr *addr, socklen_t *addrlen);
```

Questa funzione viene usata per i socket con connessione

## connect()
```c
int connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
```

Viene invocata da un client per associare un indirizzo addr a un unnamed socket sockfd.

Se l'operazione va a buon fine restituisce $0$.

# Threads

La funzione di libreria pthread_create() crea un nuovo thread
```c
int pthread_create(ptid, pattr, start, arg);
```
Il ptid è il puntatore a variabile di tipo pthread_t che conterrà l'identificatore del nuovo thread.

Il pattr è il puntatore a una variabile contenente attributi per la creazione del thread.

Il start è la funzione inizialmente eseguita dal thread

L'arg è il puntatore passato come argomento a start()

La funzione di libreria pthread_exit() termina l'esecuzione del thread che la invoca.

# Flussi di esecuzione concorrente

Data la proprietà dei thread di un processo che è quella che condividono aree di memoria alla quale possono accedere, è possibile che si verifichino modifiche concorrenti a variabili che servono nella zona critica.

Lo stato della memoria condivisa tra due o più flussi di esecuzione concorrenti dipende dall'ordine esatto degli accessi alla memoria stessa.

## POSIX Mutex

La libreria POSIX offre la MUTual EXclusion device, che è utile per proteggere strutture dati condivise e realizzare regioni critiche.

Un Mutex è un semaforo binario.

### pthread_mutex_init
```c
int pthread_mutex_init(pthread_mutex_t *mutex, const pthread_mutexattr_t *mutexattr);
```

Serve a inizializzare un mutex e imposta gli attributi a mutexattr

se mutexattr=NULL allora viene impostato il valore di default (fast).
fast: un lock blocca il thread finché il lock precedente non è rilasciato. Unlock rilascia il semaforo e ritorna subito.

So9o9 oo988c3]
### Barriera

Finché un insieme di processi o thread possa continuare a eseguirsi serve che tutti hanno raggiunto la barriera.

```c
int pthread_barrier_init(pthread_barrier_t *restrict barrier, const pthread_barrierattr_t * restrict attr, unsigned int count);
```

Questa funzione crea una nuova barriera con attributi attr e per count thread (ovvero n thread partecipano alla barriera).

Se attr=NULL allora viene impostato l'attributo di default.
- Noi useremo default.

### Condition
