___

>[!info]
>[[Keywords]], [[Inheritance]] e i [[Classes#Constructors|Constructors]] sono strettamente collegati a questo argomento. 
>
>In particolare per i [[Classes#Constructors|Constructors]] il keyword <font style="color:salmon">This</font> ha un altro significato.
>
>In particolare per i [[Polymorphism|chiamare i metodi della superclasse]] il keyword <font style="color:salmon">super</font> ha un altro significato.



# This
___

- Possiede un altro uso nei [[Classes#Constructors|costruttori]].

- La [[Keywords|keyword]] <font style="color:salmon">this</font> nel contesto dell'[[Inheritance|ereditarietà]] è usato per <font style="color:salmon">richiamare un altro costruttore della stessa classe</font>.

- Quando si usa <font style="color:springgreen">this</font> come keyword che invoca un altro costruttore, Java automaticamente <font style="color:salmon">va a cercare</font> a quale costruttore <font style="color:salmon">deve delegare la creazione dell'istanza</font>, e lo cerca guardando ai tipi degli input forniti all'interno del <font style="color:salmon">this()</font>.

- Generalmente <font style="color:springgreen">this</font> lo si usa per avere [[Overriding and Overloading|più costruttori]] che magari non chiedono in input <font style="color:salmon">tutti i campi dell'oggetto</font>.

![center](https://i.imgur.com/ihtwS87.png)

 - Se usato per <font style="color:salmon">richiamare un altro costruttore</font>, <font style="color:springgreen">this</font> deve essere <font style="color:salmon">obbligatoriamente</font> scritto nella <font style="color:salmon">prima riga del costruttore</font>.

# Super
___

- <font style="color:springgreen">super</font> può essere usato per <font style="color:salmon">chiamare i metodi delle superclassi</font>, inclusi [[Classes#Constructors|i costruttori]].

## Super to call Superclass Constructor

- Il [[Keywords|keyword]] <font style="color:salmon">super</font> è usato per <font style="color:salmon">richiamare un costruttore della superclasse</font>. (non solo)
  
  Se usato in questo modo, <font style="color:springgreen">super</font> deve essere <font style="color:salmon">obbligatoriamente</font> scritto nella <font style="color:salmon">prima riga del costruttore</font>.
![center](https://i.imgur.com/Ik74hyX.png)
 ![center](https://i.imgur.com/0l6fRus.png)

- <font style="color:salmon">Attenzione</font>: Ogni sottoclasse deve <font style="color:salmon">esplicitamente</font> avere un costruttore se la superclasse <font style="color:salmon">NON</font> fornisce un costruttore senza argomenti, che sia stato creato manualmente o di default non importa.

## Super to call Superclass Methods

>[!warning] 
>Duplicato presente anche in [[Polymorphism#Calling the Superclass Methods]]

- Per <font style="color:salmon">chiamare il metodo della superclasse</font> si usa [[This and Super#Super|super]], questa andrà a trovare e chiamare lo stesso metodo ma <font style="color:salmon">della superclasse</font>.
  ![center](https://i.imgur.com/NxHYYz3.png)