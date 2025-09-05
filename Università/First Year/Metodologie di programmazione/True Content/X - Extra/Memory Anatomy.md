___

## Cost of things in Java

- Un <font style="color:salmon">oggetto qualsiasi</font> costa un <font style="color:salmon">minimo di</font> $8$ [[Representation of data in machines|byte]]

___

Esistono due tipi di memoria:

- lo <font style="color:salmon">Heap</font>

- lo <font style="color:salmon">Stack</font>

# Heap
___

- Sullo <font style="color:springgreen">Heap</font> vanno le aree di memoria allocate per la <font style="color:salmon">creazione dinamica</font>.

- Si rappresenta l'allocazione degli oggetti.

- A ogni campo non [[Keywords|Static]] viene allocato della memoria del Heap, ma <font style="color:salmon">solo dopo l'istruzione new</font>.

# Stack
___

- Sullo <font style="color:springgreen">Stack</font> vanno le variabili <font style="color:salmon">locali</font>.

- Si rappresentano i <font style="color:salmon">frame di attivazione</font>, cioè le chiamate ai metodi, e le variabili locali.
  ![center](https://i.imgur.com/tZ3fqax.png)

# Metaspace
___

- I campi [[Keywords|Static]] di una classe <font style="color:salmon">stanno in una zona di memoria differente</font> dal Heap e dallo Stack.

- Questi esistono in <font style="color:salmon">una sola locazione di memoria</font>, allocata prima di qualsiasi oggetto della classe in una zona speciale di memoria nativa chiamata <font style="color:springgreen">Metaspace</font>.


# Esempio
___

- Mettere nel <font style="color:salmon">Metaspace</font> i blocchi per ogni campo <font style="color:salmon">Static</font>.

- Quando viene creato una nuova istanza di una [[Classes|classe]]:
  
  1) dapprima viene messo nello Stack il blocco dell'istanza.
  
  2) dopodiché si viene creare lo spazio per i [[Classes#Fields|campi]] di questa istanza, [[Default Values for Fields and Classes|inizializzati di default]], o con i valori decisi dall'utente.

  3) a questo punto si viene a creare un collegamento (freccia) dal blocco dell'istanza nello Stack <font style="color:salmon">che punta ai campi</font> di questa istanza <font style="color:salmon">presenti nello Heap</font>.

Disegno base:
![center](https://i.imgur.com/nlqUzqb.png)

Disegno da saper creare:
![[Memory allocation.gif]]
