___

In Java per controllare il flusso dell'esecuzione del programma esistono:

- Le <font style="color:salmon">istruzioni di controllo condizionali</font>.

- Le <font style="color:salmon">istruzioni di controllo iterative</font>.

# Conditionals
___

In Java i <font style="color:springgreen">condizionali</font> sono:

- <font style="color:salmon">If, Else, Else if</font>
- <font style="color:salmon">Selection operator</font> (Elvis per gli amici)
- <font style="color:salmon">Switch + Case</font>

## If, Else, Else if

- Il solito "if else".

- Else if == elif di Python.

- In Java  il <font style="color:springgreen">Else</font> si riferisce <font style="color:salmon">sempre al If subito precedente</font> se non si specifica a quale <font style="color:springgreen">If</font> riferirsi. 
  Per forzare quindi il riferimento serve utilizzare le parentesi graffe per specificare il corpo dell'<font style="color:springgreen">If</font> precedente. 

## Selection operator

- In Java esiste un <font style="color:salmon">operatore di selezione</font> (operatore condizionale), che si scrive in questo modo:
  
  `Condizione ? valoreSeVero : valoreSeFalso`
 ![center](https://i.imgur.com/R0cJ6pc.png)
## Switch + Case

- Questa istruzione serve per confrontare il valore di un'espressione intera o convertibile a [[Primitive Data Types#Int|Int]].

- [[Later Introduced things|Da Java 7 in poi]] si può anche confrontare un valore di tipo [[java.lang.String|String]].
  
  Per usarlo si scrive l'istruzione <font style="color:springgreen">Switch</font>:
  ![center](https://i.imgur.com/yTclOst.png)
  ^1
  
- [[Later Introduced things|Da Java 13 in poi]] è possibile utilizzare anche una notazione contratta con l'operatore `->` che non richiede l'utilizzo del <font style="color:salmon">break</font> per uscire:
  ![center](https://i.imgur.com/z9etXCv.png)
   ^2
- Sempre [[Later Introduced things|da Java 13 in poi]] è possibile assegnare a una variabile il risultato del <font style="color:springgreen">Switch</font>:
  ![center](https://i.imgur.com/WGyk2ae.png) ^3

- Il caso <font style="color:salmon">default</font> è il caso dove l'input non corrisponde a nessuna delle condizioni dei case precedenti.

Un altro [[Keywords|keyword]] importante da sapere quando si usano gli <font style="color:springgreen">Switch</font> è <font style="color:salmon">yield</font>:

- Questa serve quando bisogna implementare in un <font style="color:salmon">case</font> più comandi.

- Bisogna per forza assegnare lo <font style="color:springgreen">Switch</font> a una variabile se si vuole usare lo <font style="color:salmon">yield</font>.

- Bisogna per forza assegnare nello <font style="color:springgreen">Switch</font> il caso <font style="color:salmon">default</font> se si vuole usare lo <font style="color:salmon">yield</font>.

- Questa serve <font style="color:salmon">a rimpiazzare il break</font> e allo stesso tempo <font style="color:salmon">a restituire il risultato del case</font>.

 ![center](https://i.imgur.com/xFkOUUC.png)

# Iteratives
___

In Java le <font style="color:springgreen">iterative</font> sono:

- <font style="color:salmon">While</font>
- <font style="color:salmon">Do ... while</font>
- <font style="color:salmon">For</font>

Per <font style="color:salmon">uscire da un ciclo</font> anche se non è finita la sua esecuzione, serve scrivere l'<font style="color:salmon">istruzione break</font>, questa è utilizzabile solamente all'interno di un ciclo.

Per <font style="color:salmon">passare alla prossima iterazione</font>, quindi saltando il resto del ciclo corrente, serve scrivere l'<font style="color:salmon">istruzione continue</font>, questa è utilizzabile solamente all'interno di un ciclo.

## While

- Il solito <font style="color:springgreen">while</font>.

## Do ... while

- È un while ma che svolge <font style="color:salmon">almeno una</font> iterazione.

- Prima esegue il corpo del <font style="color:springgreen">Do ... while</font>, e alla fine, prima di ricominciare con il prossimo ciclo, verifica la condizione di uscita.

## For

- Il solito <font style="color:springgreen">For</font>.

La sintassi è:

- `for (<Inizializzazione>; <Espressione booleana>; <incremento>)`
  ![center](https://i.imgur.com/xQ20Vju.png)

