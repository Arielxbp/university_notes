Ogni comando possiede degli argomenti opzionali e non.

Le opzioni possono avere un argomento, scritto anche in maniere diverse:
```bash
# Per esempio per l'opzione k (key)
command -k1
command -k 1
command -key==1
```

Le opzioni senza argomento sono __raggruppabili__:
```bash
command -b -r -c
command -brc
```

## sudo

Il comando __sudo__:
- Prende come input un altro comando.
- Serve per eseguire comandi da super utente.

## su

Il comando __su__: (substitute user or switch user)
- Serve per cambiare l'utente corrente con un altro.

Se usato con l'opzione `-c` o `--command="command"`:
- Serve per eseguire un comando come un altro utente.
```bash
su -c "command" <username>

E.g.
su -c "ls /home/" aless
```

Se usato con l'opzione `-` o `-l` o `--login`:
- Serve per inizializzare una nuova shell facendo il login con l'utente specificato.

## su vs. sudo

Il comando __sudo__ permette a un'utente autorizzato a eseguire comandi come super utente o come un altro utente, __ma__ viene permessa l'operazione solo se viene autenticata inserendo la password dell'utente che vuole fare `sudo`.

## adduser

Il comando __adduser__:
- Serve per creare o aggiungere un utente esistente a un gruppo.

Se usato con l'opzione `-M` o `--no-create-home`:
- Serve per creare un nuovo utente ma __non__ crea la sua directory.

Se usato con l'opzione `-N` o `--no-user-group`:
- Serve per creare un nuovo utente ma __non__ crea un gruppo con lo stesso nome dell'utente creato.
- Deve comunque essere in un gruppo, specificato dall'opzione in questo caso obbligatoria `-g`.

## pwd

Il comando __pwd__:
- Serve per stampare sulla shell la __current working directory__ (cwd).

## cd

Il comando __cd__: (change directory)
- Serve per cambiare current working directory.

Durante la scelta del path in cui cambiare si può usare:
- `..` per indicare la directory padre.
- `.` per indicare la directory attuale.

## mkdir

Il comando __mkdir__: (make directory)
- Serve per creare una directory.

Se usato con l'opzione `-m`: (mode)
- Serve per impostare i permessi della directory. 

Se usato con l'opzione `-p`: (parent)
- Serve per creare le directory parenti se non esistono.
- Se esistono allora non produce errori.

## ls

Il comando __ls__:
- Serve per stampare la lista dei file contenuti in una directory.

Se usato con l'opzione `-a`: (all)
- Stampa la lista dei file, compresi quelli che cominciano con `.`, solitamente nascosti.

Se usato con l'opzione `-c`: (ctime)
- Se usato da solo allora sorta la lista dei file per ctime.
- Se usato con l'opzione `-l` allora fa mostrare in una colonna i rispettivi ctime e sorta per nome.
- Se usato con le opzione `-lt` allora sorta per ctime e mostra anche ctime.

Se usato con l'opzione `-l`: (long)
- Serve per stampare la lista dei file con più informazioni

Se usato con l'opzione `-u`: (atime)
- Se usato da solo allora sorta la lista dei file per atime.
- Se usato con l'opzione `-l` allora fa mostrare in una colonna i rispettivi atime e sorta per nome.
- Se usato con le opzione `-lt` allora sorta per atime e mostra anche atime.

Se usato con l'opzione `-1`:
- Serve per stampare la lista un file per riga.

Se usato con l'opzione `-i`: (inode)
- Serve per stampare l'inode number di ogni file.

## tree

Il comando __tree__:
- Serve per mostrare tramite un albero la directory.

Se usato con l'opzione `-L`: (length)
- Mostra fino alla profondità inserita.

Se usato con l'opzione `-d`: (directory)
- Mostra solo directory.

