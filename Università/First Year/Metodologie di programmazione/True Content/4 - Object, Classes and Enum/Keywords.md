___

In Java esistono i <font style="color:springgreen">Keywords</font>:
![center](https://i.imgur.com/NCkOKY8.png)

I <font style="color:springgreen">Keyword</font> più importanti sono quelli riguardanti la <font style="color:salmon">visibilità</font>:

- <font style="color:salmon">Default</font>
- <font style="color:salmon">public</font>
- <font style="color:salmon">protected</font>
- <font style="color:salmon">private</font>
>[!info]
>La visibilità ha una sua pagina apposita a questo [[Visibility|hypertext]]. 


I <font style="color:springgreen">Keyword</font> riguardanti le caratteristiche di un [[Classes#Methods|metodo]] o un [[Classes#Fields|campo]] sono:
- <font style="color:salmon">final</font> (anche per [[Classes|classi]]!)
- <font style="color:salmon">static</font>
- <font style="color:salmon">void</font> (solo per metodi) (credo)



# Final
___

- Il keyword <font style="color:springgreen">Final</font> serve per rendere "fisso" un qualcosa in Java.

## Final Constants

- Le costanti che devono essere utilizzate da altre classi solitamente sono sia <font style="color:salmon">Final</font> che <font style="color:salmon">Static</font>.

# Final Classes

- Se una classe viene definito <font style="color:springgreen">final</font>, questa <font style="color:salmon">non potrà</font> avere sottoclassi, quindi <font style="color:salmon">nessuna classe</font> può <font style="color:salmon">estenderla</font>. 

## Final Methods

- Se un metodo viene definito <font style="color:springgreen">final</font>, questa <font style="color:salmon">non potrà mai</font> essere [[Overriding and Overloading#Overriding|reimplementata/sovrascritta/overridata]] (dalle sottoclassi che hanno extendato la superclasse che possiede questo metodo <font style="color:springgreen">final</font>).

# Static
___

- Il metodo <font style="color:salmon">main()</font> è dichiarato <font style="color:springgreen">Static</font> in quanto la <font style="color:salmon">JVM</font> invoca il metodo <font style="color:salmon">main</font> ancora prima di aver creato qualsiasi oggetto.
  
  Un altro motivo è perché la classe <font style="color:salmon">potrebbe non avere un costruttore senza parametri</font> con cui creare l'oggetto.

## Static Constants

- Si usa static anche per definire costanti di classe: ovvero delle costanti che tutte le istanze hanno.

- Queste (campi) costanti possono essere chiamate sia da istanze/oggetti che dalla classe.
  
## Static Fields

- Se un [[Classes#Fields|campo]] viene dichiarato con visibilità <font style="color:springgreen">Static</font>, questa deve essere chiamata <font style="color:salmon">solamente attraverso un metodo con visibilità Static</font>.
  
  Teoricamente si può ottenere un campo <font style="color:springgreen">Static</font> da un metodo <font style="color:salmon">NON Static</font> se chiamato su un'istanza di quella [[Classes|classe]], ma ciò non è consigliato in quanto è
  <font style="color:salmon">una scrittura ambigua</font>.

## Static Methods

- Se un metodo viene dichiarato con visibilità <font style="color:springgreen">Static</font>, questa può avere all'interno del suo corpo <font style="color:salmon">solamente riferimenti a campi con visibilità Static</font>.
  (non ha senso chiamare il metodo di classe per ottenere un campo di un'istanza anche perché una classe non ha un campo d'istanza)

- Un metodo <font style="color:salmon">NON Static</font> può chiamare un altro metodo <font style="color:salmon">Static</font>.
- Un metodo <font style="color:salmon">Static</font> può chiamare un altro metodo <font style="color:salmon">Static</font>.

- Un riferimento a oggetto <font style="color:salmon">può chiamare un metodo Static</font>, anche se non è consigliato.

- Si può chiamare un metodo <font style="color:springgreen">Static</font> di una [[Classes|classe]] da una qualsiasi altra classe <font style="color:salmon">scrivendo prima del metodo Static il nome della sua classe</font>.


# Void
___

- TBD




