___

>[!info] 
>Per avere più informazioni sull'argomento andare a [[Polymorphism]].

- [[Upcasting and Downcaasting]]

# Upcasting
___

In Java per <font style="color:springgreen">Upcasting</font> si intende:

- che si può sempre considerare il tipo di un oggetto di una sottoclasse come il tipo della sua superclasse.

- È <font style="color:salmon">implicito</font>, ovvero non c'è bisogno di specificare quando si vuole upcastare.
  ![center](https://i.imgur.com/NNPSOUi.png)

## Abstract Class with Actual Object?

>[!attention] 
>Riprendendo da [[Abstract Classes]], dove si era detto che le classi astratte <font style="color:salmon">non possono avere oggetti</font>, ciò non è più vero grazie all'<font style="color:springgreen">Upcasting</font>.

- Si ricorda che <font style="color:salmon">le classi astratte non possono avere oggetti</font>. Questa affermazione è ancora circa valida, perché tramite <font style="color:springgreen">Upcasting</font> si può <font style="color:salmon">aggirare</font> questa regola.

# Downcasting
___

Invece per <font style="color:springgreen">Downcasting</font> si intende:

- che si può considerare il tipo della superclasse come un qualsiasi tipo delle sue sottoclassi.

- <font style="color:salmon">Non</font> è implicito, ovvero <font style="color:salmon">si deve sempre specificare</font> quando si vuole downcastare.

