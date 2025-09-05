___

Le <font style="color:springgreen">collezioni</font> sono strutture dati. Contengono e strutturano <font style="color:salmon">riferimenti</font> ad altri oggetti (tipicamente tutti dello stesso tipo).

# Iteration on collections
___

## External iteration

- Mediante gli <font style="color:salmon">iterator</font>

- Mediante il costrutto <font style="color:salmon">for each</font>
![center](https://i.imgur.com/BF5msC6.png)

- Mediante indici (funziona solo su liste)

## Internal iteration

- Mediante il metodo <font style="color:salmon">Iterable.forEach</font>. Questa permette l'iterazione su qualsiasi collezione senza specificare come effettuare l'iterazione.
  
  Tramite [[Polymorphism|polimorfismo]] chiamerà il forEach della classe specifica.

- forEach prende in input un <font style="color:salmon">Consumer</font>, che è un'[[Functional Interface|interfaccia funzionale]] con un solo metodo.
![center](https://i.imgur.com/tR6daVQ.png)

### Removing elements

- È possibile rimuove elementi di una collezione mentre ci si itera sopra tramite <font style="color:salmon">Iterator</font>.remove:
 ![center](https://i.imgur.com/iKhTMSt.png)
# Types of Collection

- <font style="color:salmon">ArrayList</font> -> [[ArrayList]]

- <font style="color:salmon">LinkedList</font>

- <font style="color:salmon">HashSet</font>

- <font style="color:salmon">TreeSet</font>

- <font style="color:salmon">LinkedHashSet</font>

- <font style="color:salmon">HashMap</font>

- <font style="color:salmon">TreeMap</font>

- <font style="color:salmon">LinkedHashMap</font>

# Methods for Manipulation the Collection

Questi sono alcuni metodi <font style="color:salmon">statici</font> per la <font style="color:salmon">manipolazione delle collezioni</font>:
![center](https://i.imgur.com/ZowoG3J.png)

# Collection + Consumer + Lambdas/Reference

- Le <font style="color:salmon">Collection</font> sono dotate di un metodo <font style="color:salmon">forEach</font> che prende in input un'interfaccia <font style="color:salmon">Consumer</font>\<? super T> dove T è il tipo generico della <font style="color:salmon">Collection</font>.
![center](https://i.imgur.com/bhKzPWB.png)

# What Collection should I use?

![center](https://i.sstatic.net/aSDsG.png)
