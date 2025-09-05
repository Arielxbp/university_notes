
# Linux (Introduzione)

## Shell

La shell è un programma che esegue altri comandi, cioè un __interprete di comandi__, spesso chiamata terminale.

Esistono vari tipi di shell:
- Thompson/Bourne shell __sh__.
- Bourne-Again shell __bash__. (È la default per molte distribuzioni di Linux)
- KornShell __ksh__.
- ...

## Prompt

All'interno del terminale è possibile interagire con la bash attraverso dei __comandi__.

All'inizio la bash scrive un prompt e si mette in attesa del comando dato dall'utente:
```bash
nome_utente@nome_macchina:~$ # Home directory

nome_utente@nome_macchina:~/Documents$ # After cd Documents from the home directory ~

nome_utente@nome_macchina:/$ # Root directory

nome_utente@nome_macchina:/bin$ # After cd bin from the root directory /
```

## Struttura dei comandi

Ogni comando possiede delle __opzioni__ e degli __argomenti__.

Se l'argomento è contrassegnato da {} significa che ci possono essere più argomenti.

Se l'opzione è contrassegnato da \[] significa che l'opzione è opzionale.

Le opzioni possono avere un argomento:
```bash
comando -k1
comando -k 1
comando --key=1
```

Le opzioni __senza__ argomento possono essere __raggruppate__:
```bash
comando -b -r -c
comando -brc
```

Esistono inoltre anche opzioni __BSD-style__, che sono scritti senza il dash:
```bash
tar xfz nome_file.tgz
```

## sudo (Super User Do something)

Ogni utente per poter eseguire comandi come super utente(root), ha bisogno di usare il comando sudo seguito dal comando da eseguire come super utente.

Il comando __sudo__ serve per:
- eseguire come root un comando dato in input.

## su (Switch User)

Il comando __su__ serve per:
- Apre una nuova shell con i privilegi dell'utente specificato, e per assicurarsi che si posseggono i privilegi per fare questa cosa, si richiede la password dell'utente specificato.
- e.g. per aprire una nuova shell con i privilegi di root, serve la password del root.


# Filesystem

Per filesystem si intende l'__organizzazione__ di un __area di memoria__ basata sul concetto di __file__ e __directory__.

I file possono essere:
- Regolari, cioè contengono sequenze di bit dell'area di memoria.
- Speciali a blocchi, che modellano unità di I/O a blocchi.
- Speciali a caratteri, che modellano unità di I/O a caratteri.

Linux è formato da un singolo filesystem principale. (Root /)

In una directory non è possibile:
- Avere $2$ file con lo stesso nome.
- Avere $2$ directory con lo stesso nome.
- Avere un file e una directory con lo stesso nome.
ricordando che questi nomi sono __case sensitive__.

## Path (ls)

Ogni file o directory è raggiungibile dalla directory principale tramite un path.

In Linux la tilde ~ sostituisce il path "/home/utenteX".

Per conoscere la __current working directory__, esiste il comando __pwd__.
```bash
pwd # Viene restituito la current working directory, ovvero /home/userX/dir1/.../dirZ
```

Il path __assoluto__ ha la proprietà che è valido in qualsiasi current working directory in cui si trovi attualmente la shell.

Il path __relativo__ può non essere più valido quando si cambia la current working directory.

Per avere la lista dei file contenuti in una directory si usa il comando __ls__.
```bash
ls # Restituisce la lista della cwd
ls directory_name # Restituisce la lista della directory directory_name
ls file_name # Restituisce solo file_name
ls -a # Restituisce la lista di tutti i file, anche quelli nascosti
ls -R directory_name # Restituisce la lista a partire dalla directory comprendendo tutte le sottodirectory
ls -i # Restituisce la lista includendo per ognuno anche il suo inode number
ls -l # Restituisce la lista in modo dettagliato, con permessi, utenti, byte, date, e restituisce anche la dimensione della directory in blocchi sul disco, considerando solamente la cwd e non i sottoalberi
ls -n # Stesso output del -l ma al posto dei nomi degli utenti e dei gruppi vi sono i corrispettivi id
```
Il numero presente dopo i diritti di accesso indica __il numero di directory__ all'interno della directory contanto anche le directory "." e "..", ovviamente per i file questo numero sarà $1$.

## Creazione di directory e file

### Creazione di directory (mkdir)
```bash
mkdir nome_dir # Crea una directory nell cwd
mkdir -p dir1/dir2/dir3 # Serve l'opzione -p per creare un path di directory
```

### Creazione di file (touch)
```bash
touch nome_file # Crea un file vuoto // Per definizione touch cambia i timestamp di un file
```

## Mounting (mount)

Il filesystem root / contiene molti filesystem diversi tra loro:
- Disco interno
- Filesystem di una rete.
- Filesystem di un disco esterno (usb).
- Filesystem virtuali.
- Filesystem in memoria principale (/tmp).

Il root / riesce a contenere tutti questi filesystem tramite il meccanismo del __mounting__, cioè un'operazione che viene eseguita __su una directory__ in modo tale da rendere quella directory un __punto di accesso__ per un altro (nuovo) filesystem.

La directory root del filesystem che si vuole montare __deve__ essere accessibile dalla directory alla quale viene montata.

Se la directory alla quale viene montata un altro filesystem è inizialmente vuota, allora dopo il mount conterrà l'altro filesystem.
Invece se non è inizialmente vuota, allora dopo il mount conterrà comunque l'altro filesystem, e i dati della directory non vengono sovrascritti, ma saranno accessibili solamente dopo l'unmount del filesystem montato.

## Tipi di filesystem

Il tipo di filesystem __definisce la codifica dei dati__.

Linux usa filesystem di tipo ExtX, ma può montare anche filesystem di tipo:
- NTFS
- FAT

![|600](https://i.imgur.com/87tHEbk.png)

## File passwd e group

Sono due file di testo che si trovano a:
- /etc/passwd
- /etc/group
e contengono rispettivamente:
- Tutti gli utenti.
- Tutti i gruppi.

### passwd

Ogni riga del file di testo passwd segue la struttura:
- username:password:uid:gid:gecos:homedir:shell
dove al posto della password vi è una $x$.

### group

Ogni riga del file di testo group segue la struttura:
- groupname:password:groupID:lista_degli_utenti_appartenenti
dove al posto della password vi è una $x$.

## File

Ogni file nel filesystem è rappresentato da una struttura dati __inode__ ed è identificato univocamente da un __inode number__.

La cancellazione di un file __libera__ l'inode number che può essere __riutilizzato__ per un nuovo file.

### Struttura dati inode

I principali attributi della struttura dati inode sono:
- __Type__, che indica il tipo del file.
- __User ID__, che indica l'id dell'utente proprietario del file.
- __Group ID__, che indica l'id del gruppo a cui è associato il file.
- __Mode__, che indica i permessi (read, write, execute) di accesso per il proprietario, il gruppo e per tutti gli altri.
- __Size__, che indica la dimensione in byte del file.
- __Timestamps__:
	- ctime (inode changing time), ovvero quando è stato cambiato un attributo di questo inode.
	- mtime (content modification time), ovvero quando è stato modificato il contenuto del file puntato dall'inode.
	- atime (content access time), ovvero quando è stato aperto il file puntato dall'inode.
- __Link count__, che indica il numero di __hard links__.
- __Data pointers__, che è un puntatore alla lista dei blocchi che compongono il file, o se nel caso di una directory, è un puntatore a una tabella composta da $2$ colonne:
	- Nome del file o directory.
	- L'inode number corrispondente.

## Permessi di accesso (chmod)

L'utente proprietario del file è solitamente colui che crea il file (stessa cosa per le directory).

Il gruppo proprietario è il gruppo __primario__ dell'utente proprietario.

### Per i file

Il proprietario definisce i permessi di accesso, ovvero:
- Chi può __leggere__.
- Chi può __scrivere__, cioè sovrascrivere, appendere e cancellare il file.
- Chi può __eseguire__.

### Per le directory

![|750](https://i.imgur.com/VJffS9C.png)

### Permessi speciali

Esistono $3$ permessi speciali:
- __Sticky bit__.
- __Setuid bit__.
- __Setgid bit__.
che possono essere applicati a file e directory.

Questi possono essere assegnati tramite il comando __chmod__ e vengono visualizzati al posto del bit di esecuzione.
Ora se il permesso di esecuzione c'è, allora la $s$ o la $t$ saranno __minuscoli__.
Se il permesso di esecuzione __non__ c'è, allora la $s$ o la $t$ saranno __maiuscoli__.

```bash
chmod 0777 nome_file # Il primo 7 indica che l'utente ha i permessi rwx, il secondo 7 stessa cosa ma per il gruppo dell'utente, e il terzo 7 stessi permessi ma per tutti gli altri, lo 0 indica che non viene assegnato nessun permesso speciale

chmod 4777 nome_file # Il 4 indica che viene assegnato il setuid bit, '100 binario'='4 decimale'
```

#### Sticky bit

È inutile sui file.

Normalmente nelle directory con solo i permessi di write ed execute, si possono cancellare i file contenuti in essa, anche se non si hanno i permessi di scrittura sul file.

Se si applica lo sticky bit su queste directory, si viene a correggere questo comportamento, permettendo la cancellazione di file __solo se__ si hanno i permessi di scrittura su di essi.

#### Setuid bit

Si usa solo per i __file eseguibili__.

Se un file possiede il setuid bit, allora quando verrà eseguito il processo corrispondente, tale processo possederà i privilegi dell'__utente proprietario__ del file e __non__ quelli dell'utente che ha eseguito il file.

Per esempio quando si cambia password, il comando passwd possiede lo setuid bit per poter cambiare il file con i privilegi del proprietario, ovvero del root. (L'utente non può modicare il file passwd per ragioni di sicurezza)

#### Setgid bit

È l'analogo del setuid bit ma per i gruppi.

Può essere applicato anche a una directory, e in questo caso ogni file creato all'interno della directory che ha il setgid bit avrà il gruppo della directory invece che quello del gruppo primario dell'utente che ha creato il file.

## Cambiare proprietario e gruppo (chown e chgrp)

Il comando __chown__ serve per cambiare il proprietario di un file o directory e/o il gruppo di tale file o directory.

Il comando __chgrp__ serve per cambiare solamente il gruppo di un file o directory.

```bash
chown nome_proprietario file1 file2 file3 ... # Cambia il proprietario dei file
chown -R nome_proprietario {file} # Cambia il proprietario in modo ricorsivo (sottoalberi)
chown nome_proprietario:nome_gruppo {file} # Cambia sia il proprietario che il gruppo
chown :nome_gruppo {file} # Cambia solo il gruppo

chgrp nome_gruppo {file} # Cambia il gruppo dei file
chgrp -R nome_gruppo {file} # Cambia il gruppo dei file e dei sottoalberi
```

## umask (Permessi di accesso default)

L'umask serve per __modificare__ i permessi di accesso __default__ dati a file e directory al momento della loro creazione.

Quindi se di default i file vengono creati con i permessi di accesso "$777$", applicando un umask di valore "$002$", si andrà a cambiare i permessi di accesso di default per i file a "$775$" (rwxrwxr-x).

## cp (Copiare file e directory)

Il comando __cp__ serve per:
- Copiare un file sorgente verso un file destinazione.
- Copiare multipli file sorgenti verso una directory.

```bash
cp file_sorgente file_destinazione
cp {file_sorgenti} nome_directory
cp -r nome_directory nome_directory
cp -i sorgente destinazione # Interactive, per essere avvisati prima di sovrascrivere
cp -u sorgente destinazione # La sovrascrittura avviene solo se il mtime del file sorgente è più recente di quello del file destinazione
```

## mv (Muovere un file in una directory / Rinominare un file)

Il comando __mv__ serve per:
- Muovere un file in una directory.
- Rinominare un file.

```bash
mv old_file_name new_file_name
mv file directory
mv {file} directory
mv -f file directory # Force, non dare nessun avviso (prompt) prima di sovrascrivere
mv -i file directory # Interactive, per essere avvisati prima di sovrascrivere
mv -u file directory # Update, per sovrascrivere solo se il mtime del file è recente dello stesso file presente nella directory destinazione
```

## rm (Rimuovere un file o directory)

Il comando __rm__ serve per:
- Rimuovere file.
- Rimuovere directory.

```bash
rm file
rm directory
rm -i file # Interactive
rm -r directory # Ricorsivo, quindi elimina anche i sottodirectory
rm -f file # Force, ovvero forza l'eliminazione senza chiedere e/o dare promp
```

## ln (Creare link di file)

Il comando __ln__ serve per:
- Creare symbolic link. (È un puntatore al nome del file senza contenere in esso il contenuto)
- Creare hard link. (È un puntatore verso l'inode che contiene i dati del file)

Un __hard link__ può solo riferirsi a un file presente nello stesso filesystem.
Un __symbolic link__ punta alla locazione o al path del file originale.

Se si rimuove la sorgente di un hard link:
- Il hard link funziona ancora e contiene ancora i dati del file sorgente.

Se si rimuove la sorgente di un symbolic link:
- Il soft link non funziona più in quanto non esiste il file puntato da essa. (Tipo shortcut di Windows)

```bash
ln file_sorgente link_file_sorgente_nome # Crea un hard link
ln file_sorgente # Crea un hard link nella stessa directory
ln -s file_sorgente link_file_sorgente_nome # Crea un symbolic link
```

## touch (Cambiare i timestamps di un file)

Il comando __touch__ serve per:
- Aggiornare gli attributi timestamp di un file al tempo attuale. (default senza -t)
- Modificare gli attributi timestamp di un file.
- Ha come effetto collaterale che se non esiste il file indicato dal path allora lo crea.

```bash
touch {file} # Cambia il timestamp dei file a quello attuale
touch -t timestamp file # Cambia il timestamp con quello specificato
touch -m file # Cambia solo il tempo di ultima modifica
touch -a file # Cambia solo il tempo di ultimo accesso
```

## du (Stimare lo spazio usato dal file o directory)

Il comando __du__ serve per:
- Avere una stima di quanto spazio viene usato da un file o anche multipli.
- Avere una stima di quanto spazio viene usato da una directory o più directory.

```bash
du # Restituisce le dimensioni delle sottodirectory della cwd (non i file)
du -c # Restituisce le dimensioni delle sottodirectory e di ogni file presenti nel sottoalbero della cwd
du file # Restituisce solo la dimensione di quel file
du directory # Restituisce le dimensioni della directory specificata e delle sue sottodirectory ma non i file all'interno
du -c directory # Restituisce il totale delle dimensioni del sottoalbero a partire dall directory data insieme al resto delle dimensioni
du -a directory # Restituisce oltre alle dimensioni di ogni directory e sottodirectory, anche quello di ogni singolo file
du -s # Restituisce solo il totale della directory
du -h directory # Restituisce le dimensioni con la loro unità di grandezza
du --exclude=./path # Restituisce le dimensioni ma escludi la directory con quel path
du --exclude=estensione # Restituisce le dimensioni ma escludi quelli con quella estensione
```

__Attenzione__ in quanto il comando __du__ usato su un __symbolic link__ restituisce la dimensione del symbolic link in numero di blocchi su disco.

	Per avere lo stesso numero del file puntato dal symbolic link è necessario aggiungere l'opzione `-D` che sta per dereference

## df (Mostrare informazioni sui filesystem)

Il comando __df__ serve per:
- Mostrare la dimensione dei filesystem montati sul dispositivo.
- Mostrare l'attuale uso dei filesystem montati sul dispositivo.

```bash
df # Mostra le informazioni di tutti i filesystem montati attualmente
df -h # Mostra le informazioni di tutti i filesystem montati attualmente e le dimensioni sono date insieme alla loro unità di grandezza
df -l # Mostra solamente tutti i filesystem locali
df -i # Mostra le informazioni di tutti i filesystem ma in base agli inode presenti in ogni filesystem
df file # Mostra le informazioni riguardo al filesystem montato che contiene il file indicato
df directory # Mostra le informazioni riguardo al filesystem montato che contiene la directory indicata
```

## dd (Copiare, convertire e formattare un file)

Il comando __dd__ serve per:
- Creare file in modo elaborato.
- Copiare file in modo elaborato.

In particolare serve per __copiare file speciali__ che __non__ possono essere copiati tramite il comando __cp__.

È molto utile per:
- Cancellare __completamente__ tutti i dati da un supporto di memoria (tutti 0).
- Copiare solo __una parte__ di un file.
- Preparare un file a essere __formattato__.

```bash
dd if=file_sorgente of=file_destinazione # dd legge da if e la destinazione di dd è data da of, l'input può essere anche una partizione o una directory
dd bs=dimensione_di_singolo_blocco_di_bytes_sulla_quale_operare # La dimensione impatta le performance e il tempo dell'operazione
dd count=un_integer # Rappresenta il numero di blocchi di dimensione bs da copiare
dd conv=CONVS # Copia il file usando un modificatore che converte il dato che legge in base a CONVS

dd if=file_IN of=file_OUT bs=integer seek=integer count=integer # Il seek serve per skippare i primi x blocchi bs, e count serve per indicare quanti blocchi bs copiare
```

## mkfs (Crea un filesystem sul dispositivo)

Il comando __mkfs__ serve per:
- Creare un filesystem sul dispositivo.
- È anche detto __formattazione__ in quanto prepara la partizione a memorizzare i file secondo un dato formato (e.g. ext4).

```bash
mkfs file_creato_con_dd # Usa di default -t ext2
mkfs -t ext4 file_creato_con_dd # Crea un filesystem di tipo ext4 in directory_name
mkfs -t ext4 device # Se è un device allora non deve essere già montato
```

# Processi

Un file eseguibile che è attualmente __in esecuzione__ viene chiamato __processo__.

Quindi:
- La __bash__ è un processo.
- Molti dei comandi sono processi.
- Ma __non__ tutti i comandi creano dei processi.

Un file eseguibile può essere eseguito più volte contemporaneamente, dando vita a un nuovo processo ogni volta.

## Rappresentazione dei processi

Un processo viene rappresentato dal:
- PID, che è un identificatore univoco del processo.
- PCB, che è il Process Control Block, una struttura dati univoca che mantiene tutti gli identificatori che interessano il processo, l'umask del file eseguibile e la prorità del processo stesso.
- $6$ aree di memoria.

### PID (Process Identifier)

Il __PID__, o __Process IDentifier__, è un identificatore univoco di un processo.

Ciò vuol dire che in un dato istante, __non__ ci possono essere $2$ processi con lo stesso PID.

Quando invece un processo termina, il PID assegnatoli viene __liberato__ e quindi può essere riassegnato a un nuovo processo.

### PCB (Process Control Block)

IL PCB è una struttura dati univoca per ogni processo che contiene:
- Tutte gli identificatori che interessano il processo:
	- PID, identifica il processo.
	- PPID, identifica il parente del processo.
	- Real UID, identifica l'utente che esegue il processo.
	- Real GID.
	- Effective UID, identifica l'utente con la quale il sistema deciderà i permessi del processo. (Quindi può cambiare in base al setuid, se è settato allora RUID!=EUID, dove EUID sarà l'UID del proprietario del file, mentre RUID sarà dell'altro utente che sta cercando di eseguire questo programma).
	- Effective GID.
	- Saved UID, è l'identificatore salvato del real UID dopo che viene cambiato tramite il setuid.
	- Saved GID.
- La current working directory.
- L'umask del file eseguibile del processo.
- La priorità del processo, ovvero la priorità con la quale il processo verrà scelto dallo scheduler per runnare sulla CPU.

### Aree di memoria di un processo

Le $6$ aree di memoria di un processo sono:
- __Text Segment__, che contiene le istruzioni da eseguire in linguaggio macchina.
- __Data Segment__, che contiene i dati statici inizializzati, ovvero le variabili globali e locali static, insieme ad alcune costanti.
- __BSS__ (Block Started from Symbol), che contiene i dati statici __non__ inizializzati. Questa distinzione serve per motivi di __realizzazione hardware__.
- __Heap__, che contiene i dati dinamici (allocati tramite funzioni come malloc e simili).
- __Stack__, che contiene le chiamate a funzioni, con i corrispondenti dati dinamici come variabili locali __non__ static.
- __Memory Mapping Segment__, che contiene tutto ciò che riguardano le librerie esterne dinamiche usate dal processo. Può fungere anche come estensione del Heap in alcuni casi.

Alcune aree di memoria possono essere condivise:
- Text Segment tra più istanze dello stesso processo viene condiviso.
- Tra due processi si possono avere lo stesso BSS o Data Segment o MMS.
mentre altre no:
- Lo stack __non è mai condiviso__.

## Stato di un processo

Un processo può essere nei stati:
- __Running__, cioè in esecuzione sul processore.
- __Runnable__, cioè pronto per l'esecuzione, in attesa che lo scheduler lo scelga. (Non è in attesa di alcun evento e.g. I/O)
- __(Interruptible) Sleep__, cioè quando è in attesa di un qualche evento. (e.g. Lettura di blocchi dal disco)
- __Zombie__, cioè quando il processo è terminato e le sue $6$ aree di memoria non sono più in memoria ma il suo PCB viene ancora mantenuto dal kernel perché il processo padre non ha ancora richiesto il suo "exit status".
- __Stopped__, cioè quando il processo riceve un segnale di STOP, andando in caso particolare di sleeping, attendendo quindi un segnale di CONT (continue).
- __Traced__, cioè quando è in esecuzione di debug, oppure quando in generale è in attesa di un segnale (altro caso particolare di sleeping).
- __Uninterruptible sleep__, cioè quando il processo sta facendo operazioni di I/O e non può essere ne interrotto ne ucciso.

### jobs

Il comando __jobs__ serve per:
- Mostrare lo stato dei jobs nella sessione corrente.

È possibile usare il comando per mostrare __solamente__ i PID dei processi.

```bash
jobs # Mostra tutti i job

jobs -l # Mostra tutti i job in modo più dettagliato

jobs -p # Mostra solamente i PID dei processi.
```

## Modalità di esecuzione di un processo (foreground e background)

La modalità __foreground__:
- Può leggere l'input da tastiera.
- Può scrivere su schermo.
- Non restituisce il prompt finchè non termina.
- Non si possono far eseguire altri comandi mentre esiste questo processo in foreground.

La modalità __background__:
- Non può leggere l'input da tastiera.
- Può scrivere su schermo.
- Restituisce immediatamente il prompt.
- Si possono far eseguire altri comandi mentre esiste questo processo in background.

Per interrompere un processo in foreground viene usato CTRL+z, che in verità invia un segnale di SIGSTOP.

Se si manda un segnale di SIGSTOP a un processo sleep, __il comando sleep continua a contare i secondi__.

### bg

Il comando __bg__ serve per:
- Portare un processo in background.

```bash
bg # Porta in background il job che ha il numero più alto
bg %numero_del_job # Per numero del job non si intende l'ID del processo ma il numero del job che parte da 1
```

### fg

Il comando __fg__ serve per:
- Portare un processo in foreground.

```bash
fg # Porta in foreground il job che ha il numero più alto
fg %numero_del_job
```

## ps (Mostrare informazioni dei processi in esecuzione)

Il comando __ps__ serve per:
- Mostrare le informazioni dei processi in esecuzione.

```bash
ps # Mostra i processi dell'utente attuale lanciati dalla shell corrente
ps numero_pid_di_un_processo
ps {numeri_pid_di_processi}
```

### top (ps interattivo)

Il comando __top__ serve per:
- Avere un ps ma interattivo.

## kill (Inviare segnali a un processo)

Il comando __kill__ serve per:
- Inviare segnali a un processo (non solo la terminazione).

Un processo prende in considerazione il segnale inviato solo se tale segnale viene inviato dal real user del processo, o se proviene da un superuser.

Un processo che riceve un segnale:
- O fa un'azione predefinita in base al segnale ricevuto.
- O fa un'azione personalizzata in base al segnale ricevuto.

```bash
kill -segnale_come_integer pid # Il segnale può essere indicato tramite un intero, e.g. SIGKILL=9
kill -s SIG_nome_segnale pid # Tipo SIGKILL
kill -s nome_segnale pid # Tipo KILL
kill -s SIG_nome_segnale %numero_del_job # Come in bg e fg
```

### Segnali SIGSTOP e SIGSTP

Servono per __sospendere__ processi.

CTRL+z invia un segnale di SIGSTOP.

### Segnali SIGCONT

Serve per __far continuare processi sospesi__.

### Segnali SIGKILL e SIGINT

Servono per __terminare__ processi.

CTRL+c invia un segnale di SIGINT.

### Segnali SIGUSR1 e SIGUSR2

I segnali SIGUSR1 e SIGUSR2 sono impostati per essere __configurati dall'utente__ per le proprie necessità.

Questi segnali consentono una semplice forma di comunicazione tra processi.

## nice (Lanciare comandi con priorità modificata)

Il comando __nice__ serve per:
- Lanciare comandi con niceness (attributo presente nel PCB che indica la priorità del processo) modificata.

La priorità va da:
- $-20$, priorità più alta possibile.
- $19$, priorità più bassa possibile.

```bash
nice # Mostra il niceness di partenza (default a 0)
nice -n valore_niceness_custom comando # Lancia comando con niceness uguale al valore indicato
```

### renice (Modificare il niceness di processi in esecuzione)

Il comando __renice__ serve per:
- Modificare il niceness di processi già in esecuzione.

```bash
renice valore_niceness_custom {pid}
```

## strace (Lanciare comandi visualizzando le sue syscall)

Il comando __strace__ non incluso tra i comandi base serve per:
- Lanciare un comando visualizzando __tutte__ le sue system call.

Può essere usato anche per visualizzare le system call di processo dato il suo PID.

```bash
strace comando # Per lanciare comandi e visualizzare le syscall
strace -p pid # Per visualizzare le syscall di un comando già in esecuzione
```

# C

## Ambiente di sviluppo

Il linguaggio C prevede l'uso di:
- Editor, per scrivere il programma.
- Preprocessor, per preprocessare il codice del programma (direttive, elimina commenti).
- Compiler, per tradurre il codice preprocessato in codice macchina eseguibile direttamente dall'hardware.
- Linker, per unire tutti i codici compilati insieme alle librerie usate, in un singolo file eseguibile che viene salvato su disco.

## Ambiente di esecuzione

I programmi C tramite:
- Loader, carica il programma eseguibile in memoria primaria.
- CPU, esegue ogni istruzione del programma in memoria.

## Compilare un programma

```bash
gcc prog_name.c # Solo compilazione
gcc -Wall prog_name.c # Vengono stampati tutti i messaggi di warning se ci sono
gcc -Wall prog_name.c -lm
```

- L'opzione __Wall__ sta per "Warning All".
- L'opzione __l__ sta per "Linker"
	- Quindi `-lm` indica al compiler di linkare una specifica libreria, in questo caso la libreria "m", che sarebbe per le funzioni matematiche "math".

Il risultato del comando `gcc prog_name.c` è un file eseguibile.

Per specificare il nome dell'output: `gcc prog_name.c -o output_name.o`

### (Solo) Precompilazione

Per fare solo la precompilazione: `cpp prog.c > precomp.c`
- Il `>` serve per redirectare l'output del comando in un file `precomp.c`
- Senza il `>` il comando stamperebbe sul terminale tutto il programma precompilato.

### (Solo) Compilazione (di un precompilato)

Per fare solo la compilazione di un precompilato: `gcc -c precomp.c -o comp.o`

### Precompilazione e compilazione del precompilato

Per fare la precompilazione e compilazione del precompilato: `gcc -c file.c -o file.o`
- L'opzione `-c` indica che il comando si deve fermare dopo aver compilato, quindi di non eseguire il linking, cioè si ferma dopo aver creato il file oggetto.

### (Solo) Linking

Per fare solo il linking di un compilato: `gcc file.o`

Per fare il linking di più file: `gcc file1.o ... fileN.c`
- Si possono mischiare file .c (sorgenti) e file .o (oggetti)

## Sequenze di escape \\

Per muovere il cursore __all'inizio della prossima riga__: `\n`

Per muovere il cursore __all'inizio della riga attuale__: `\r`

Per muovere il cursore __di una tabulazione__: `\t`

Il `\f` __è uguale (o simile)__ al `\n`.

## Variabili

Una variabile __è una locazione di memoria__.

A una variabile possono essere attribuiti modificatori:
- Signed, cioè con segno (sia numeri positivi che negativi).
- Unsigned, cioè senza segno (solo numeri positivi e lo zero).
- Short, cioè con meno bit.
- Long, cioè con più bit.
- Const, cioè costante, non modificabile dopo la sua inizializzazione.

### Variabili (e costanti) non valide

Qualsiasi variabile che:
- Comincia con un numero __non è valida__.
- Comincia con $ __non è valida__.
- Contiene & __non è valida__.
- Contiene - __non è valida__.
- Contiene spazi __non è valida__.
- È una parola riservata __non è valida__.
- È lunga più di $31$ caratteri __non è valida__.

### Booleani

Nel linguaggio C i booleani come tipo di dato base non esiste.

Senza usare librerie si usano i numeri $0$ e $1$.

Usando la libreria `<stdbool.h>` si possono usare i valori `true` e `false`.


## Placeholder per variabili

Per le variabili di tipo integer: `%d` o `%i`.

Per le variabili di tipo long: `%l`.

Per le variabili di tipo integer in esadecimale: `%x`.

Per le variabili di tipo float: `%f`.

Per le variabili di tipo float in notazione scientifica: `%e`.

Per le variabili di tipo double: `%lf`.

## Input da terminale (scanf)

L'istruzione `scanf` serve per leggere l'input dal terminale per inserirlo in una locazione di memoria (variabile).

```c
scanf(formato, locazione_di_memoria);

scanf(formato, nome_di_variabile); // DA NON FARE, scanf deve avere la LOCAZIONE DI MEMORIA, e NON il valore della variabile nella quale inserire l'input
```

Il formato contiene placeholder che dicono a scanf in che tipo di dato la stringa in input viene convertita.

Il valore che scanf restituisce:
- Se è un intero positivo, allora è il numero di input letti e assegnati con successo.
- Se è l'intero zero, allora indica che non sono stati assegnati gli input in quanto non combaciavano con il tipo del placeholder.
- Se è `EOF` (solitamente l'intero $-1$), allora indica che è accaduto qualcosa che ha fermato lo scanf prima che scanf abbia iniziato la conversione dell'input.

## Operatori

Aritmetici:
- `+`
- `-`
- `*`
- `/`
- `%`

Relazionali (Boolean):
- `==`
- `!=`
- `<`
- `<=`
- `>`
- `>=`

Logici:
- `!` è il __not__.
- `&&` è il __and__.
- `||` è il __or__.

Bitwise:
- `&` è il __and bit a bit__.
- `|` è il __or bit a bit__.
- `~` è il __not bit a bit__.
- `^` è il __xor__.

Shift:
- `<<` è il __shift dei bit verso sinistra__. (e.g. un numero diventa più grande)
- `>>` è il __shift dei bit verso destra__. (e.g. un numero diventa più piccolo)

```c
// Un intero ha dimensione 16 bits
int numero = 7; // 0000 0000 0000 0111 in binario
numero = numero<<3; // 112 decimale in quanto 0000 0000 0011 1000
numero = 7;
numero = numero>>1; // 3 in decimale in quanto 0000 0000 0000 0011
```

## Tipo del risultato di una divisione

Il risultato di __ogni__ operazione dipende dai tipi di dato degli operandi.

In particolare il risultato di una divisione avrà lo stesso tipo dell'operando più grande __in termini di tipi di dato__.

## Troncamento di numeri

Se il valore effettivo è maggiore in termini di tipi di dato, tale valore viene troncato nel tipo di dato dichiarato durante l'inizializzazione dela variabile.

E.g. `int x =3.14` non darà nessuno warning e semplicemente la variabile conterrà solo $3$.

## Pre-incremento e Post-incremento

Il __pre__-incremento di un intero è dato da:
- `++x`

Il __post__-incremento di un intero è dato da:
- `x++`

## Loops

Nel linguaggio C esistono $3$ tipi di costrutti iterativi, cioè loops:
- __while__.
- __for__.
- __do-while__, è un while dove il corpo del loop viene eseguito almeno una volta.

### while

Nel while la __condizione__ viene valutata __prima__ di entrare nel loop.

### do-while

Nel do-while la __condizione__ viene valutata __alla fine__ del loop.

```c
do {
	// corpo del loop
} while (condizione);
```

### break

Il break si usa per:
- Terminare un loop indipendentemente dal valore della condizione.
- Uscire da uno __switch__.

### continue

Il continue si usa per:
- Passare subito alla prossima iterazione.

## Stringhe

Una stringa è un __array di caratteri__ speciale:
- Ogni elemento dell'array è un carattere della stringa.
- L'ultimo elemento dell'array è il __NULL Terminator__, rappresentato da `\0`

E.g. una stringa "Test" è un array composto in questo modo: `['H','e','l','l','o',\0]`

Da ricordare che un array di caratteri __che non contiene alla fine il__ `\0` __non è una stringa__.

```c
char str[10] = "test"; // I rimanenti posti liberi sono indeterminati ma è ok

char str[] = "test"; // Viene allocata una stringa di dimensione 5 e non 4 in quanto si conta anche il \0
```

### strcpy

È una funzione usata sulle stringhe, che serve per:
- Copiare una stringa.

#### strncpy

È un'altra versione della funzione `strcpy` dove si copiano al più n byte del source.

```c
strcpy(char *dst, char *src);

strncpy(char *dst, char *src, size_t n);
```

### strcat

È una funzione usata sulle stringhe, che serve per:
- Concatenare due stringhe.

#### strncat

È un'altra versione della funzione `strcat` dove si concatenano al più n byte del source.

```c
char dst[] = "Te";
char src[] = "st";

				   "Te"          "st"
strcat(char *dst, char *src); // Il risultato è in dst ed è Test

strncat(char *dst, char *src, size_t n);
```

### strcmp

È una funzione usata sulle stringhe, che serve per:
- Confrontare due stringhe.

#### strncmp

È un'altra versione della funzione `strcmp` dove si confrontano al più n byte del source.

```c
int strcmp(char *dst, char *src);

int strncmp(char *dst, char *src, size_t n);
```

## Input / Output (File)

Il linguaggio C presenta alcune funzioni per leggere e scrivere/stampare su:
- File.
- Standard input/output stream.

### Input

La funzione __puts__ scrive sullo __standard output__ una stringa seguita __automaticamente__ da un newline escape sequence `\n`.

La funzione __fputs__ scrive sullo stream dato come argomento una stringa.

```c
int puts(const char *s);

int fputs(const char *s, FILE *stream);
```

### Output

La funzione __fgets__ legge fino a un dato numero di caratteri dallo stream una stringa e smette di leggere appena legge un newline.

```c
//                                                           stdin o nome_di_un_file_aperto
char *fgets(char *s, int n_da_leggere, FILE *stream);

// Per tutte le righe di un file aperto

while (fgets(buffer, sizeof(buffer), file_aperto) != NULL) {
	// Faccio qualcosa con la riga letta contenuta nel buffer
}
```

## Puntatori

I puntatori sono __variabili__ che contengono l'__indirizzo di una locazione di memoria__.

Il __valore diretto__ è l'indirizzo di memoria dove si trova il dato.

Il __valore indiretto__ è il dato che sta in quell'indirizzo di memoria.

Quindi:
- `&var` è l'indirizzo di memoria.
- `*var` è cosa è contenuto in quell'indirizzo.

E.g.
```C
int num = 5;
int *numPtr; // Adesso è ancora NULL

numPtr=&num; // Assegno alla variabile puntatore l'indirizzo di memoria della variabile num
*numPtr=10; // Assegno alla variabile puntata dalla variabile puntatore il valore 10
```

È possibile aumentare tramite operazioni matematiche l'indirizzo di memoria di una variabile puntatore:`numPtr+=1`. (Nota l'assenza del \* a numPtr)

### Vettori (Array) e puntatori

Il puntatore a un array è uguale a un puntatore al primo elemento dell'array.

```c
char str[] = "Test";
char *ptr;

// Stessa cosa
ptr = str;
ptr = &str[0];
```

## Allocazione dinamica di memoria

Gli array e le altre variabili sono allocate __nello stack__ a tempo di __compilazione__.

A __runtime__ (dinamicamente quindi) gli array e le altre variabili sono allocate __nell'heap__.

Per allocare a runtime memoria si usano:
- Malloc.
- Calloc.
e per liberarla successivamente si usa:
- free.

```c
void *malloc(size_t numero_in_bytes_da_allocare);

void *calloc(size_t numero_elementi_da_allocare, size_t dimensione_di_un_elemento_da_allocare);

void free(void *ptr);
```

Da notare che serve fare il __casting__ dei puntatori restituiti da queste `malloc` e `calloc` al tipo di puntatore relativo __al tipo di dato contenuto__ nella memoria per poter utilizzare correttamente l'__aritimetica dei puntatori__.

## Struct (ures)

Una struttura serve per definire nuovi tipi di dato che combinano tipi di dato misti.

Per usare uno struct bisogna prima definirla.

È legale durante l'inizializzazione di uno struct inizializzare meno campi.

### Passaggio delle struct come parametri a funzione

Se il passaggio viene fatto per valore (\*):
- Ha il vantaggio di essere semplice.
- Ha lo svantaggio che i dati vengono __copiati__ nello stack.

Se il passaggio viene fatto per riferimento (&):
- Ha il vantaggio che i parametri non vengono memorizzati nello stack.

# Programmazione di sistema

Il Kernel è la componente del sistema operativo che __gestisce le risorse disponibili__ e offre l'accesso e l'utilizzo delle risorse da parte dei processi.

Queste risorse che offre sono:
- CPU, il processore.
- RAM, la memoria principale.
- I/O, ovvero i dispositivi di input e di output.

Le __system call__ sono dei __punti di accesso__ al Kernel, cioè permettono a un processo che li usa di accedere ai servizi offerti dal Kernel.


Nel linguaggio C le system call possono essere chiamate tramite le funzioni di libreria del sistema. Queste funzioni invocheranno il corrispondente servizio del Kernel attraverso __interrupt__ per il Kernel usando istruzioni macchina.

Le informazioni ottenibili tramite il comando `man` sulle syscall si trovano nella __sezione 2__ del `man`.

Da notare che le funzioni di libreria generali __non__ sono punti di accesso ai servizi del Kernel, ma sono semplicemente delle funzioni che possono invocare o non delle syscall.

E.g. l'istruzione `printf` può usare la syscall `write` per scrivere una stringa in output.
E.g. le istruzioni `atoi` e `strcpy` __non__ usano syscall.

Le informazioni ottenibili tramite il comando `man` sulle funzioni generali si trovano nella __sezione 3__ del `man`.

## Differenza tra syscall e funzioni generali

Sia le syscall che le funzioni generali sono __funzioni C__.

Entrambe __forniscono servizi__ a un'applicazione.

Una funzione generali __può essere rimpiazzata__ ma una syscall __no__.

## System call (syscall)

Le syscall si differenziano per il compito che svolgono in:
- Quelle riguardanti __file__.
- Quelle riguardanti la __gestione della memoria__.
- Quelle riguardanti i __processi__.

### errno (variabile di errore per syscalls)

È una variabile __globale__ che rappresenta il __codice di errore__ dell'__ultima__ syscall invocata che ha generato un errore.

Ha senso quindi utilizzare tale variabile solo dopo essersi accertati che la syscall abbia restituito un valore di errore, solitamente $-1$, altrimenti si rischia di __considerare il valore di errno inconsistente__.

### perror (funzione generale di libreria)

La funzione `perror` della libreria `stdio.h` serve per:
- Stampare su __stderr__ il messaggio di errore convertendo il codice di errore `errno` in una stringa.

```c
void perror(const char *prefix);
```

Il parametro `prefix` viene stampato insieme alla stringa di errore ma prima di essa.

### strerror (funzione generale di libreria)

La funzione `strerror` della libreria `string.h` serve per:
- Convertire un codice di errore `errno` dato in input nella sua equivalente rappresentazione in stringa.

## Syscall sulla gestione della memoria

### mmap, brk, sbrk (syscalls)

La syscall `mmap` serve per:
- Allocare memoria. Crea un'area di memoria per __mappare__ un file a partire da un indirizzo specificato e con un livello di protezione indicato in input.
- Mappa un file su disco in un area di memoria (buffer).
- Gestire il memory-mapped I/O.

La syscall `brk` serve per:
- Cambiare la dimensione del data segment del processo. 

La syscall `sbrk` serve per:
- Aumentare la dimensione del data segment del processo.

È possibile che l'area di memoria usata dopo un `realloc`, e quindi `sbrk`, sia diversa dall'area di memoria usata prima del `realloc`, in quanto se il Kernel non riuscisse ad allargare l'area di memoria attualmente puntata, andrebbe ad allocare una nuova area, andando a liberare quella attualemente puntata.

### memset, memcpy (funzioni generali di libreria)

La funzione `memset` serve per:
- Assegnare un valore intero (integer) a un numero di byte contigui di un area di memoria.

La funzione `memcpy` serve per:
- Copiare un numero di bytes contigui a partire da un'area di memoria verso un'altra.
- Le due aree di memoria __non__ devono sovrapporsi.


### msync (syscall)

La syscall `msync` serve per:
- Scrivere sul file presente nel disco le modifiche fatte sul file che stanno in memoria principale.
- Solamente se il flag `MAP_SHARED` è settato, questa flag indica se le operazioni sulla memoria modificano il file.

### munmap (syscall)

La syscall `munmap` serve per:
- De-mappare pagine di memoria.

## Syscall sui file

Quando un processo termina, va a chiudere __automaticamente__ tutti i file correntemente aperti. (Tuttavia è buona regola chiudere esplicitamente un file)

### File descriptor

È il riferimento a un file aperto, rappresentato da un intero, generato sequenzialmente a partire dal valore $0$.

Di default __ogni processo__ ha associato i seguenti file descriptor:
- $0$ per stdin.
- $1$ per stdout.
- $2$ per stderr.

Quando un file viene chiuso, il suo file descriptor viene __liberato__ e quindi può essere riutilizzato.

È possibile aprire uno stesso file e ottenere file descriptor __diversi__ ma che puntano __allo stesso file__.

### File flags associati ai file descriptor

I file status flags sono:
- Associati allo stato di un file.
- Condivisi tra tutti i file descriptor ottenuti per duplicazione da un unico file descriptor.

I file descriptor flag:
- Sono associati al file descriptor.
- Sono indipendenti dal contenuto o status del file.
- Descrivono proprietà e comportamente delle operazioni effettuate sul file.
- Sono individuali per ogni file descriptor.

### open (syscall)

La syscall `open` serve per:
- Aprire un file.

La differenza tra `open` e `fopen` è che `fopen` restituisce un puntatore a un oggetto di tipo `FILE`. Questo oggetto è normalmente una struttura che contiene le informazioni richieste dalla libreria `stdio` per gestire lo stream.

### read (syscall)

La syscall `read` serve per:
- Leggere un file.

Richiede come parametri in input:
- Un file descriptor `fd`.
- Un puntatore a un buffer (area di memoria) in cui memorizzare i byte letti `buf`.
- Il numero di byte da leggere `count`.

Restituisce il numero di byte letti o $-1$ se errore. (Può essere minore di `count`)

La differenza tra `read` e `fread` è che `fread` legge da uno stream di tipo `FILE`, quindi bufferizzata, e legge sapendo la dimensione del tipo di dato da leggere.
Mentre `read` non legge in modo bufferizzato e lavora sui byte indipendentemente dal tipo di dato in essi contenuto.

### write (syscall)

La syscall `write` serve per:
- Scrivere in un file.

Richiede come parametri in input:
- Un file descriptor `fd`.
- Un puntatore a un buffer (area di memoria) da cui leggere i dati da scrivere `buf`.
- Il numero di byte da scrivere `count`.

Restituisce il numero di byte scritti o $-1$ se errore. (Può essere minore di `count`)

### close (syscall)

La syscall `close` serve per:
- Chiudere il file descriptor `fd` dato in input.

Restituisce $0$ se va a buon fine oppure $-1$ in caso di errore.

Nel caso venga chiuso l'ultimo file descriptor che fa riferimento a un file rimosso, allora __il file viene cancellato__.

### dup (syscall)

La syscall `dup` serve per:
- Duplicare il file descriptor `old_fd` dato in input.

Restituisce il valore del nuovo `fd` oppure $-1$ in caso di errore.
Tale valore sarà diverso da `old_fd`. (Da ricordare che i valori dei file descriptor sono degli interi)

### fcntl (syscall)

La syscall `fcntl` serve per:
- Manipolare un file descriptor dato in input.
	- Duplicazione del `fd`.
	- Manipolazione del flag file descriptor.
	- Manipolazione del flag di stato.
	- Gestione lock sul `fd`.

### select (syscall)

La syscall `select` serve per:
- Monitorare uno o più file descriptor, rimanendo in attesa che almeno uno di essi sia disponibile per effettuare l'operazione richiesta.

## Syscall sui processi

`Init` è il processo $0$ (ha `pid=1`), ed è il padre di __tutti__ i processi del sistema __in esecuzione__.

Da essa vengono creati tutti i processi mediante la syscall `fork`.

La creazione consiste nella __duplicazione del processo__ e nella __creazione della relazione padre-figlio__.

Quando un processo nasce:
- Eredita codice e parte dello stato dal processo padre.

Quando un processo termina o muore:
- Ritorna l'exit status al processo padre.

Nel caso il processo padre muoia prima del processo figlio:
- Il figlio viene adottato da `Init`.

### Zombie (processo)

Un processo quando termina:
- Dallo stato __running__ invia l'exit status al padre e cambia nello stato __zombie__.

Quindi un processo zombie __è un processo terminato__, ma il cui PCB è mantenuto nella Process Table dal Kernel per dare modo al processo padre di __leggere l'exit status__ di tale processo.

Ora se il padre di un processo muore o termina:
- Il processo figlio __rimane__ nello stato zombie.

Un processo figlio effettivamente termina quando:
- Il processo padre riceve l'exit status.

### fork (syscall)

La syscall `fork`:
- Crea un nuovo processo che è la copia del processo chiamante, meno alcune sue strutture dati, e.g. il suo `pid`.
- Restituisce un valore intero (integer) che indica il pid del processo figlio se il `fork` restituisce un valore diverso da $0$ (questo nel processo padre), mentre restituisce $0$ come pid al processo figlio per indicare al processo figlio che egli è il processo figlio.

In caso di errore la syscall restituisce $-1$ al chiamante e __non__ viene creato nessun processo figlio.

Il processo figlio eredita:
- RUID.
- EUID.
- RGID.
- EGID.
- GID.
- Working directory.
- Ambiente (env) del processo padre.
- Descrittori dei file.
- Terminale di controllo.
- Memoria condivisa.
ma __non__ eredita:
- PID.
- PPID.
- Timers.
- Lock ottenuti.
- Contatori dell'utilizzo delle risorse.
- Coda dei segnali.


### \_exit (syscall)

La syscall `_exit`:
- Termina direttamente il processo che la invoca senza invocare nessun handler.
- Chiude tutti i file descriptor.
- Se viene terminato ma i figlio sono ancora in esecuzione allora vengono ereditati dal processo $1$, ovvero `Init`.
- Invia il segnale `SIGCHLD` al processo padre la terminazione è di un processo figlio.
- Ritorna `status` e l'exit status al processo padre.

### exit (funzione generale di libreria)

La funzione `exit`:
- Invoca tutti gli handler registrati.
- Chiude tutti i file descriptor. (tramite syscall `_exit`)
- Svuota gli stream `stdio` e li chiude.
- Termina il processo. (tramite syscall `_exit`)
- Ritorna `status & 0377` al processo padre se la terminazione è di un processo figlio. (tramite syscall `_exit`)

### abort (funzione generale di libreria)

La funzione `abort`:
- Invia `SIGABRT` per il processo chiamante.

Se un processo riceve un `SIGABRT` allora esso termina in __modo anormale__.

La `SIGABRT` può essere intercettata e gestita.

### wait (syscall)

La syscall `wait`:
- Sono usate per attendere cambiamenti di stato in un figlio del processo chiamante.
- Sono usate per ottenere informazioni sul figlio il cui stato è cambiato.

Questi cambiamenti di stato avvengono quando:
- Il figlio è __terminato__.
- Il figlio è stato __arrestato__ da un __segnale__.
- Il figlio è stato __ripristinato__ da un __segnale__.

Se un figlio è terminato:
- La syscall `wait` permette al sistema di rilasciare le risorse (PCB) associate al figlio.
- Se non viene eseguita un'attesa il figlio terminato rimane nello stato zombie.

### waitpid (funzione generale di libreria)

La funzione `waitpid`:
- Sospende l'esecuzione del processo chiamante fino a quando un figlio specificato tramite il suo pid dato in input non cambia input.

Il comportamento default di `waitpid` è di attendere solo i figli terminati, ma questo è modificabile attraverso l'argomento `option` in input:
- `WNOHANG` torna immediatamente se nessun figlio è uscito.
- `WUNTRACED` torna anche se un figlio si è arrestato.
- `WCONTINUED` torna anche se un figlio arrestato è stato ripreso inviando `SIGCONT`.
Questi valori `W****` possono essere messi in __or__ logico.

### execve (syscall)

La syscall `execve`:
- Sostituisce l'immagine del processo con quella contenuta nel `filename` dato come input, dove il `filename` è un file binario o uno script.

Quando si effettua una `fork`, il processo figlio è una simil-copia del padre, e solitamente si vuole far eseguire __qualcosa di diverso__ dal padre al figlio.
Per fare ciò si possono usare delle condizioni di flusso `if-else` ma sarebbe __poco efficiente__.

Per questo viene usato la syscall `execve` o le funzioni generali di libreria `exec`.

Gli attributi che `execve` __preserva__ dal fork originale sono:
- PID.
- PPID.
- RUID.
- RGID.
- GID.
- Session ID.
- Terminale di controllo.
- Working directory.
- Root directory.
- Umask del file alla sua creazione.
- Lock sui file.
- File descriptors.
- Maschera dei segnali.
- Segnali in attesa.
e __non preserva__:
- EUID.
- EGID.
- Mapping delle zone di memoria.
- Timers.
- Memoria condivisa.
- Lock sulle zone di memoria.

### chdir, chroot (funzioni generali di libreria)

Queste funzioni sono usate se si vuole cambiare la __working directory__ o la __root directory__ di un processo.

## Socket

I __socket__ consentono la comunicazione tra __processi__ nel paradigma client/server.

Il server:
- Definisce il socket.
- Presenta dei dati noti ai client. (e.g. nome di file o indirizzo di rete)
- Accetta connessioni sul socket da parte di uno o più client.
	- Ricava un __file descriptor__ sulla connessione.

Il client:
- Definisce il socket.
- Crea una connessione sul socket.
	- Ricava un __file descriptor__ sulla connessione.

## Syscall per i socket

I socket presentano $4$ system calls:
- `socket`, serve per creare una struttura dati della socket.
- `bind`, serve per associare un nome alla socket.
- `listen`, serve per mettere un processo in ascolto su una socket.
- `accept`, serve per accettare una connessione su una socket.

## Tipologia socket

Le tipologie di socket sono definite da $3$ attributi:
- Domain (o family), ovvero la __modalità del collegamento__:
	- `AF_LOCAL`, cioè client e server devono risiedere sulla stessa macchina.
	- `AF_INET`, cioè client e server comunicano in rete con protocollo __IPV4__.
	- `AF_INET6`, cioè client e server comunicano in rete con protocollo __IPV6__.
- Type, ovvero la __semantica del collegamento__:
	- `SOCK_STREAM`, cioè per avere un flusso bidirezionale di byte affidabile basato su connessione (socket TCP).
	- `SOCK_DGRAM`, cioè per supportare comunicazioni datagram, senza connessione (socket UDP) e con sequenze inaffidabili di messaggi.
	- `SOCK_RAW`, cioè per l'accesso diretto (raw socket) alle comunicazioni di rete.
- Protocol, ovvero il __protocollo usato__:
	- (Per il corso viene impostato a $0$).

```c
int sd =socket(AF_INET, SOCK_STREAM, 0);
```

### listen (syscall)

La syscall `listen` serve per:
- Marcare il socket `sockfd` come passivo, ovvero pronto a ricevere richieste mediante una `accept()`.

La syscall restituisce $0$ in caso di successo e $-1$ in caso di errore.

```c
int listen(int sockfd, int backlog);
```

### accept (syscall)

La syscall `accept`:
- Viene usata __per i socket con connessione__, quindi __non__ per `SOCKET_DGRAM`.
- Estrae la prima richiesta di connessione nella coda delle richieste in attesa sulla coda di listening del socket `sockfd`.
- Crea un nuovo socket con connessione e ritorna un nuovo file descriptor. Il nuovo socket __non è in ascolto__.
- Il socket `sockfd` continua a svolgere le sue funzioni.

```c
int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
```

### connect (syscall)

La syscall `connect`:
- Viene invocata da un client per associare un indirizzo `addr` a un __unnamed socket__ `sockfd`.

Se la syscall va a buon fine restituisce $0$ e quindi `sockfd` può essere utilizzato come file descriptor per leggere e scrivere sul server.

```c
int connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
```

`addrlen` è la __dimensione__ di `addr`, ovvero `sockaddr`.

