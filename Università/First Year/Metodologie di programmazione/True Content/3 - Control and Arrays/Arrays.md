___

- Un <font style="color:springgreen">Array</font> rappresenta un <font style="color:salmon">gruppo di variabili</font> tutte dello <font style="color:salmon">STESSO tipo</font>.

- Gli Array <font style="color:salmon">sono oggetti</font>. Quindi le variabili di Array contengono il <font style="color:salmon">riferimento</font> all'Array.

- Gli <font style="color:salmon">elementi</font> di un Array possono essere <font style="color:salmon">tipi primitivi</font> oppure <font style="color:salmon">riferimenti a oggetti</font>, <font style="color:salmon">inclusi altri Array</font>.

- Esempio di creazione di un Array di Int senza valori:
  ![center](https://i.imgur.com/Lg3teQo.png)

- Se si vuole creare un Array di Int con valori in input
  ![center](https://i.imgur.com/8XO2RmD.png)

- Non serve per forza scrivere "new int\[]":
  ![center](https://i.imgur.com/vPNUB34.png)

- In Java <font style="color:salmon">NON è possibile specificare la dimensione accanto al nome dell'Array</font>:
  ![center](https://i.imgur.com/jtMo74Z.png)

- Per <font style="color:salmon">accedere</font> a un elemento dell'Array bisogna <font style="color:salmon">specificare il nome dell'Array e l'indice dell'elemento</font>:
  
  Questo indice può essere anche un'<font style="color:salmon">espressione</font>.
  ![center](https://i.imgur.com/XUOmA9X.png)

- Un Array ha <font style="color:salmon">dimensioni prefissate</font> che <font style="color:salmon">NON possono essere modificate</font>.
  
  È possibile creare un nuovo Array con <font style="color:salmon">nuove dimensioni</font> a partire da un Array preesistente attraverso il [[Classes#Methods|metodo]] [[Keywords|statico]] <font style="color:salmon">copyOf</font> della [[Classes|classe]] "java.util.Arrays"


- Si possono creare <font style="color:salmon">Array a due dimensioni</font> (matrice) specificando due coppie di parentesi quadre:
  ![center](https://i.imgur.com/xlN4A9I.png)

- [[Later Introduced things|A partire da Java 5]] si possono dichiarare metodi con <font style="color:salmon">un numero variabile di parametri</font>:
  ![center](https://i.imgur.com/PvP8dKj.png)
  L'argomento passato al metodo è di fatto un riferimento ad un Array, chiamato in questo caso <font style="color:salmon">values</font>.
  
  È possibile specificare altri parametri, ma <font style="color:salmon">PRIMA dell'UNICA sequenza variabile di parametri</font>:
  ![center](https://i.imgur.com/7E4NMP5.png) ^1

- L'Array possiede il [[Polymorphism|polimorfismo]] mentre l'[[ArrayList]] no

- ![center](https://i.imgur.com/224Hc9p.png)

# Methods for Manipulating Arrays

Questi sono alcuni metodi statici per la manipolazione degli Array:
![center](https://i.imgur.com/hAPPhN1.png)

Da ricordare in particolare è il metodo <font style="color:salmon">asList</font>.