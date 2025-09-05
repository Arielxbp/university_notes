___

>[!info]
>[[Classes]] e [[Autoboxing and Auto-Unboxing]] sono strettamente collegate a questo argomento. 
>

- Le <font style="color:springgreen">classi Wrapper</font> permettono di <font style="color:salmon">convertire i valori di un tipo</font> [[Primitive Data Types|primitivo]] in [[Classes#Objects|oggetti]].

- Forniscono <font style="color:salmon">metodi di accesso</font> e <font style="color:salmon">visualizzazione</font> dei valori.

 ![center](https://i.imgur.com/fX92z1V.png)

## Comparing Integers

Dato che ora i numeri possono essere sotto forma di <font style="color:salmon">Integer</font>, e non più un tipo primitivo, serve usare al posto di "$==$" i metodi:

- <font style="color:salmon">equals()</font>, che restituisce <font style="color:salmon">true</font> se e solo se l'oggetto in input è un intero di valore uguale al proprio.

- <font style="color:salmon">compareTo()</font>, che restituisce:
  1) $0$ se sono uguali.
  2) $<0$ se il proprio valore è <font style="color:salmon">minore</font> di quello in ingresso.
  3) $> 0$ se il proprio valore è <font style="color:salmon">maggiore</font> di quello in ingresso.
  
