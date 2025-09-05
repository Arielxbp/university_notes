
# Ambiente di sviluppo

- Non è un linguaggio interpretato, ma compilato

# Ambiente di esecuzione

- Il loader carica in memoria il programma
- La CPU esegue ogni istruzione

# Differenze tra altri linguaggi

- Eseguibile anche senza interprete (non lo ha)

# Struttura di un programma

- Deve esistere una funzione principale chiamata "main.c"
- Codice organizzato in funzioni identificati univocamente
- La funzione principale e le altre funzioni possono risiedere nello stesso file .c o anche in file .c diversi che verranno poi linkati insieme

# Funzione

```c
<return-type> function_name(parameter-list){
...
}
```

- il valore di ritorno di una funzione può essere un'altra funzione

## Headers
```c
#include <stdio.h>
```

- Sono direttive per il pre-processore
- I file header contengono costanti, funzioni prototipo
- Se il file è tra <> allora il file va cercato all'interno dei file header standard
- Se il file è tra "" allora il file è dell'utente e va cercato all'interno della directory attuale o specificato dall'utente
- Usando l'opzione -I si può specificare le directory in cui cercare gli header file

# Compilare ed eseguire

- Per fare tutto tramite un solo comando (precompilazione, compilazione e linking)
```shell
gcc file.c -o executable.o
```

- Per fare solo precompilazione
```shell
cpp file.c > precompiled_file.c
```

- Per fare solo compilazione di un precompilato
	- Durante la compilazione si controlla la sintassi del programma
```shell
gcc -c precompiled_file.c -o compiled_file.o
```

- Per fare solo precompilazione e compilazione insieme
```shell
gcc -c file.c -o file.o
```

- Per fare solo linking di un compilato
	- Durante il linking vengono risolte tutte le chiamate a funzione
```shell
gcc compiled_file.o -o executable_file.out

# linking di più file compilati
gcc file1.o file2.o -o executable_file.out
```

- Per eseguire il file esecutabile
```shell
./executable_file.out
```

# Input/Output

- Tutte le funzioni essenziali per l'I/O sono nel file stdio.h

## Output

- printf
- Si usa \n

## Input

- scanf
- Viene letto da tastiera o altro dispositivo e memorizzato in variabili

# Variabili ed espressioni

## Variabili

- Quando una variabile viene dichiarata, viene allocato in uno spazio di memoria, sia se viene inizializzata o meno
- Una variabile può essere inizializzata o meno
- Una variabile o più variabili possono essere stampate all'interno di un printf attraverso l'uso di placeholder piazzati all'interno della stringa da stampare
```c
printf("printing numbers: %d, %d\n", x, y)
```

- Variabili dichiarate all'interno degli header di una funzione si chiamano parametri

- Una variabile può essere costante attraverso il keyword "const"
```c
const int x
```

### Tipi di dati per i numeri

- Per i numeri interi si usano
```c
short
int
long
```

- Per i numeri reali si usano:
```c
float
double
long double
```

### Tipi di dati per i booleani

- Richiedono l'uso di <stdbool.h> se si vuole usare variabili "True" e "False"
- In alternativa basta usare i valori:
	- 0 per false
	- 1 o diverso da 0 per true

## Espressioni

- La funzione printf restituisce il numero di caratteri stampati
- La funzione scanf restituisce il numero di valori letti

# Operazioni aritmetici

- A

## Divisione

- Il risultato dipende dai tipi di dato degli operandi
- Il risultato è dello stesso tipo dell'operando più grande in termini di tipi di dato

## Incrementi
```c
intVar++
intVar--
++intVar
--intVar
```

# Loops

```c
while
for
do while
```

## While

- Se il body è una sola istruzione si possono omettere le parentesi graffe

## For

- bruh

## Do while

- Esegue il body del loop almeno una volta

# String

```c
char string[size_of_string] = "string"

char string[size_of_string] = {"s","t","r","i","n","g","\0"} // Ok

char string[size_of_string] = {"s","t","r","i","n","g"} // Non ok

char string[] = "string" // char string[6]

```
- È un array di char	
- L'ultimo elemento dell'array deve contenere il carattere speciale \\0
- Il carattere speciale nell'inizializzazione di una stringa in modo esplicito non viene aggiunto automaticamente
- È possibile non indicare un numero preciso da allocare per l'array, in tal caso verrà allocato automaticamente pari alla grandezza della stringa
- Per comparare due stringhe non è possibile usare l'operatore \==, ma serve usare la funzione strncmp

# Puntatori

- Sono __variabili__ che contengono l'indirizzo di una locazione di memoria
- Il puntatore punta sempre al primo byte della locazione di memoria della variabile
- Il __valore diretto__ di una variabile puntatore è l'indirizzo di un'altra cella di memoria
- Il __valore indiretto__ di una variabile puntatore è il valore contenuto dalla cella di memoria il cui indirizzo è contenuto nel __valore diretto__
- 

```c
int num=5; // variabile normale int alla quale assegno 2 byte
int *numPointer=&num; // variabile puntatore alla quale assegno l'indirizzo di memoria della variabile normale num
*numPointer=10; // nella cella di memoria di num metto 10 invece che 5
```

## Vettori e puntatori
```c
int vect[10];
int *ptr=NULL;
ptr=&vect[0];
ptr=vect;

```

- Un puntatore assegnato al vettore punta al primo elemento del vettore
- 

# Allocazione dinamica della memoria
```c
// Per allocare memoria per un vettore di interi di 10 elementi
void *calloc(10, 4)
void *malloc(40)
void free(void *ptr)
```

- Per allocare memoria si usa __calloc__ o __malloc__
- Dopo aver finito di usare la memoria è sempre bene liberarla usando __free__

# Structure
```c
struct{
	double x; // variabile 1
	double y; // variabile 2
} point2D; // nome della variabile struct
```
- Le strutture servono per definire tipi di dato che contengono un certo numero di campi di tipi diversi
- Sono tipo dei contenitori di più variabili di vari tipi

## Tagged structure

- as

## Type-defined structure

- asd

# File I/O
```c
// per eseguire file con argomenti da file di testo
$ ./my_program < input.txt
```

## File di testo

- Ogni riga del file di testo finisce con \n
- Il file di testo finisce con EOF (end of file)

- Per usare un file di testo servono le funzioni definite in stdio.h
- Il file da disco viene portato nel buffer, solo quando si salva il file il buffer scrive tutto ciò che è stato temporaneamente scritto nel buffer nel file.
- Altrimenti quando si riempie il buffer questa scriverà sul file

```c
// fopen(const char *pathname,  const char *mode)
// mode tra r, w, a, r+, w+
// w e a creano il file se non esiste
// r+ e w+ aprono entrambe in R/W mode
// per aprire un file
FILE *fp=fopen("file.txt", "r");

// se eseguito correttamente il puntatore cambia invece di essere NULL
// quindi si esegue sempre un controllo
if (fp==NULL){
	printf("Error opening file\n");
	exit(1);
}
```

```c
int fscanf(); // per leggere da file

int fprintf(); // per scrivere nel file la stringa printata

char *fgets(); // per leggere fino al primo \n

int fputs(); // per scrivere sul file

int feof(); // restituisce 0 quando trova EOF
```