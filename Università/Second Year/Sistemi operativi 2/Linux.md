

installare le pagine del man

ls 
ls -l
ls -a
cp per copiare item
mkdir per creare una directory nella directory attuale
ps per avere una lista dei processi in esecuzione al momento
ps -e per avere i processi in esecuzione sul sistema
ps -p \$$ -o cmd h per mostare solo la colonna del cmd e togliere ide
\$$ serve per 

su : fa un cambio di utente per eseguire l'istruzione richiesto
sudo su - : serve per fare un cambio utente a root, cambia la shell da utente a root
whoami : mostra chi è attualmente l'utente della shell
cd : ci riporta alla home directory
cd / : per andare alla directory di root
~ : rappresenta la path /home/utente, quindi ~/cartella dentro
pwd : current working directory
il path assoluto parte da /home
la directory . : rappresenta la directory /home/utente
la directory .. : rappresenta la directory /home

posso fare cd Pictures/../Pictures/cartelladentroPictures, con questa istruzione cd va a Pictures, torna indietro dato che ce .., riva in Pictures e poi va nella cartelladentroPictures

tree : serve a visualizzare la directory e le sub in modo grafico

mkdir -p directory/da/creare : usare -p per creare tutte le directory scritte

touch directory : crea una directory(contenitore) totalmente vuoto
mkdir directory: invece crea una directory contenente almeno . e ..

il filesystem root, cioè /, contiene elementi dei vari filesystem esterni se inseriti tramite il sistema del mouting

partizione significa suddividere logicamente un disco

mount : serve per montare un fs
mount da sola serve per visualizzare i fs sul sistema
mkfs \[-t type fsoptions] device : è il comando per creare un fs su un device

nel file group all'interno di /etc ci sono scritti i gruppi del sistema
una riga è composta così: sudo:x:27:username
la prima colonna è il nome del gruppo
la seconda è la password del gruppo
la terza è il id del gruppo
la quarta sono i nomi degli utenti appartenenti a quel gruppo

ls -l mostra per le directory la dimensione del blocco allocato a quel diirectoy
ls -l mostra solamente nella colonna del numero di directory di una directory solamente il numero di directory di quella directory, ma magari dentro a quelle directory ce ne saranno altre.
la scritta totale numerox quando si scrive ls -l indica il numero totale di blocchi allocati

-----

# 12/03

```bash
ls -la
# mostra una lista delle directory e i dettagli di ognuna, incluse le directory nascoste
```

- per cancellare file non serve solamente avere permessi in scrittura ma anche particolari permessi

- Se su una directory si ha solamente il permesso di esecuzione, allora si può attraversa tale directory

- Se su una directory si ha solamente il permesso in lettura, allora si può solo listarne il contenuto e non si può attraversarci

- Se su una directory si hanno tutti i permessi, cioè lettura, scrittura ed esecuzione, allora si può cancellare anche file presenti all'interno di tale directory anche senza avere permessi di scrittura su tale file.
  Ciò è prevenibile usando lo sticky bit.

- Usando lo sticky bit su una directory si previene la cancellazione di un file all'interno di tale directory se non si hanno permessi per cancellare tale file

- Quando si esegue un file eseguibile, tale file si esegue come se fossimo l'utente proprietario di tale file, non come l'utente che lo sta eseguendo.
  Ciò è prevenibile attraverso il setuid bit.

- Il setgid bit è analogo al setuid bit ma per i gruppi.
  Inoltre applicando tale bit su una directory, i file creati all'interno di tale directory avrà come gruppo il gruppo della directory invece del gruppo del proprietario del file

```bash
chmod xxxx fileName
# xxxx sono i numeri in ottale(quindi da 0 a 7) che indicano i permessi sul file

chmod u+rwx fileName
# per farlo usando simboli
```

```shell
sudo chown [userName | userUID] fileName
# sta per change owner

```

```shell
chgrp
# sta per change group
```

```shell
umask [mode]
# setta i diritti di accesso al file o alle directory al momento della loro creazione
# cioè definisce i diritti dei file o directory che verranno creati in quel
```


```shell
cp
# copy file or directory
```
-a serve per preservare tutti gli attributi del file dalla quale si copia
senza -a il file copiato ha gli attributi del umask attuale

```shell
mv
# move
```
-f di default è attivo, cioè sovrascrive il file se nella destinazione esiste un file con nome uguale

```shell
rm
# remove
```

```shell
ln file linkName
```

# du

```shell
du
# quanto è usato il disco
```

- Gli hard link vengono usati di default
- Se un documento viene cancellato ma il suo inode aveva degli hard link allora l'inode del documento rimane
- Solamente quando non ci sono più hard links allora l'inode viene cancellato
- Dato un inode, esistono molti file puntati da tale inode

# df

```shell
df directory
	
```
# dd

```shell
dd [options]

#options:
#bs = legge e scrive il numero indicato di bytes
#seek = scrive nel file output a partire dal numero indicato
#skip =
#count = indica il numero di bytes

```

- può essere usato per creare file in modo elaborato
- serve per copiare file speciali che non si riescono a copiare attraverso l'istruzione copy
- serve per copiare parti di file
- può essere usato per cancellare completamente i dati da un supporto di memoria
- può essere usato per pulire un disco attraverso la sovrascrittura di soli zeri

# mkfs

```shell
mkfs [-t type fsoptions] device

#
```

# Processo

- Un processo è un file eseguibile
- Quando si esegue un comando vengono creati processi (non tutti i comandi)

## Redirect dell'output

- I simboli > e < possono essere usati per redirigere l'output di un comando su di un file

- Ad esempio con i seguenti comandi:
  si è rediritto l'output del comando "ls -la" all'interno del file "file.txt" 
```shell
touch file.txt
ls -la > file.txt
cat file.txt
```

## PID (Process IDentifier)

- È un identificatore univoco di un processo
- Un processo una volta terminato, il suo PID viene liberato e pronto per essere riusato da un altro processo
- Ogni processo possiede un PPID (Parent Process IDentifier)

## Stato di un processo

- Se in esecuzione: Running
- Se pronto per essere eseguito: Runnable
- Se in attesa di qualche evento (i.e. lettura di blocchi da disco): Interruptible sleep
- Se è terminato e non più in memoria ma il suo PCB è ancora mantenuto dal kernel: Zombie
- Se ha ricevuto un segnale STOP, è un caso particolare di sleep: Stopped
- Se è in esecuzione di debug, o in attesa di un segnale, è un caso particolare di sleep: Traced
- Se è in uno statop di sleep ma non interrompibile: Uninterruptible sleep

## Foreground / Background (Modalità di esecuzione dei processi)

- Un processo eseguito in __foreground__ prende controllo del prompt e non lo rilascia finchè non finisce di eseguire
- Un processo eseguito in __background__ rilascia immediatamente il controllo del prompt
- Usando CTRL+Z si può interrompere un processo eseguito in foreground
- Usando il comando bg mentre esiste un processo interrotto da CTRL+Z porta il processo a eseguirsi in background
- Usando il comando fg mentre esiste un processo in background porta il il processo a eseguirsi in foreground
- Inserendo & alla fine di un comando permette di far eseguire il processo in background

# Segnali

```shell
kill [-l [signal]] [pid]

# kill -l : serve a mostrare la lista dei signali
 ```

- I segnali vengono presi in considerazione solamente se il real user del processo è lo stesso di colui che invia il segnale (o se inviato dal superuser)
- SIGKILL per effettuare una terminazione non voluta
- SIGINT è simile al SIGKILL ma il processo terminato è fatto bene
- Esistono due segnali disponibili all'utente per effettuare operazioni personalizzate attraverso i segnali, SIGUSR1 e SIGUSR2

# 