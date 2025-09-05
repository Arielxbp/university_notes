___
>[!attention] 
>Riguardare [[Upcasting and Downcasting]] e [[Inheritance]] in quanto vi sono alcune similarità.

>[!tldr] 
>Questa è una pagina generale sulle <font style="color:springgreen">interfacce</font>, per <font style="color:springgreen">interfacce specifiche</font>:
>[[Iterable and Iterator Interfaces]]

- Le <font style="color:springgreen">interfacce</font> in Java consentono a più classi di <font style="color:salmon">fornire e implementare un insieme di metodi</font> comuni.

- Le <font style="color:springgreen">interfacce</font> specificano <font style="color:salmon">solamente il comportamento</font> che un certo oggetto deve fare.
  
  Permettono di <font style="color:salmon">modellare comportamenti comuni</font> a classi che non sono necessariamente in relazione gerarchica. ([[Is-a and Has-a#Is-a|Is-a]])

  Nel momento in cui una classe <font style="color:salmon">X</font> decide di implementare un'interfaccia <font style="color:salmon">Y</font>, tra le due classi si instaura una relazione di tipo [[Is-a and Has-a#Is-a|Is-a]], ovvero <font style="color:salmon">X è di tipo Y</font>.

- L'<font style="color:salmon">implementazione</font> di tali [[Classes#Methods|metodi]], ovvero il corpo, <font style="color:salmon">invece rimane non definito</font>, e viene lasciato il compito di implementarlo alle <font style="color:salmon">classi che implementeranno</font> l'interfaccia.
  
  Sempre se non queste non sono <font style="color:salmon">Static</font> o <font style="color:salmon">default</font>, se lo sono è possibile specificare i dettagli implementativi.

Le <font style="color:springgreen">interfacce</font> sono [[Abstract Classes|classi astratte]]:

- sempre se non si definiscono <font style="color:salmon">metodi di default</font>, cosa possibile [[Later Introduced things|da Java 8 in poi]].
- sempre se non si definiscono <font style="color:salmon">metodi statici</font>, cosa possibile [[Later Introduced things|da Java 8 in poi]].
- Sempre se non si definiscono <font style="color:salmon">metodi privati</font>, cosa possibile [[Later Introduced things|da Java 9 in poi]].

Un'<font style="color:springgreen">interfaccia</font> è una <font style="color:salmon">classe</font> che può contenere <font style="color:salmon">solo</font>:

- Costanti.
- [[Abstract Methods|Metodi astratti]].
- Rispettivamente:
  Java 8 -> Metodi di default, metodi statici.
  Java 9 -> Metodi privati.

- Tutti i metodi dichiarati in un'interfaccia sono <font style="color:salmon">implicitamente</font>: [[Visibility#Public|public]] e [[Abstract Methods|abstract]].
  
- Tutti i [[Classes#Fields|campi]] dichiarati in un'interfaccia sono implicitamente: [[Visibility#Public|public]], [[Keywords#Static|static]] e [[Keywords#Final|final]].

![center](https://i.imgur.com/dLmPZVN.png)

- Una classe può implementare un'interfaccia tramite il keyword <font style="color:salmon">implements</font>.

- Una classe che implementa un'interfaccia decide di voler <font style="color:salmon">esporre pubblicamente</font> all'esterno il comportamento descritto dall'<font style="color:springgreen">interfaccia</font>.

- È <font style="color:salmon">obbligatorio</font> che ogni metodo implementato abbia <font style="color:salmon">esattamente</font> lo <font style="color:salmon">stesso tipo di ritorno</font> e di <font style="color:salmon">visibilità</font>.

- <font style="color:salmon">Ricorda</font>: usare "<font style="color:salmon">@Override</font>" quando implementare metodi presi dalle interfacce.

>[!danger] 
>Una classe che implementa un'interfaccia può essere assegnato a una variabile del tipo dell'interfaccia per [[Upcasting and Downcasting]].
>![center](https://i.imgur.com/odf1G4x.png)

# Difference between Interfaces and Abstract Classes
___

Le classi <font style="color:salmon">abstract</font> possono sembrare <font style="color:salmon">molto simili</font> alle [[Interfaces|interfacce]] in quanto:

- <font style="color:salmon">Impongono</font> delle funzioni che ogni classe <font style="color:salmon">deve</font> implementare.

- Le interfacce vengono usate nelle classi attraverso il [[Keywords|keyword]] <font style="color:salmon">implements</font>, simile al <font style="color:salmon">extends</font> delle [[Inheritance|superclassi]]. 

Però <font style="color:salmon">ci sono delle differenze</font>:

- Si possono implementare <font style="color:salmon">infinite</font> interfacce ma si può estendere <font style="color:salmon">una sola classe</font>.

- Nelle interfacce <font style="color:salmon">tutti i campi</font> devono essere inizializzati in quanto sono [[Keywords|static]] e [[Keywords|final]], quindi <font style="color:salmon">hanno un valore prefissato</font>, fisso per ogni oggetto.
  
  Questo <font style="color:salmon">non vale</font> per le superclassi, che <font style="color:salmon">hanno campi propri</font> per ogni oggetto.

# Default and Static Methods for Interfaces
___

## Default Methods for Interfaces

- È possibile specificare delle implementazioni di default di metodi <font style="color:salmon">non statici</font> tramite il [[Keywords|keyword]] <font style="color:salmon">default</font>.

- I metodi di default sono stati introdotti per <font style="color:salmon">non rompere il codice che utilizza le versioni precedenti di interfacce</font>. (dato che così non devono per forza implementarle)

## Static Methods for Interfaces

- È possibile specificare delle implementazioni di <font style="color:salmon">metodi statici</font> nelle <font style="color:springgreen">interfacce</font>.

- <font style="color:salmon">Attenzione</font>: i [[Keywords#Static Methods|metodi static]] <font style="color:salmon">non funzionano</font> con il [[Polymorphism|polimorfismo]].

- Sono metodi di utilità non associati alle singole istanze.

# Private Methods for Interfaces
___

- Per facilitare il riuso del codice, da Java 9 <font style="color:salmon">è possibile definire metodi privati</font> all'interno di un'<font style="color:springgreen">interfaccia</font>.

- Tipicamente questi metodi vengono invocati in metodi di default.