___

>[!info] 
>[[Inheritance]], [[Overriding and Overloading]], [[This and Super]] sono strettamente collegati a questo argomento.
>
>[[Upcasting and Downcasting|Upcasting and Downcasting]]

- È uno dei concetti cardine della programmazione orientata ad oggetti.

- Attraverso questo concetto, una variabile che ha il tipo della [[Inheritance|superclasse]] può contenere un riferimento a un oggetto <font style="color:salmon">che ha il tipo di una qualsiasi delle sue sottoclassi</font>:
  ![center](https://i.imgur.com/NNPSOUi.png)

- La selezione del metodo da chiamare <font style="color:salmon">avviene in base all'effettivo tipo</font> dell'oggetto riferito dalla variabile.

- Il <font style="color:springgreen">polimorfismo</font> implementa il <font style="color:salmon">binding dinamico</font>, in quanto <font style="color:salmon">l'associazione</font> tra una variabile riferimento e il metodo viene stabilito <font style="color:salmon">a tempo di esecuzione</font>.

# Calling the Superclass Methods
___

>[!warning]
> Duplicato presente anche in [[This and Super#Super to call Superclass Methods]]

- Per <font style="color:salmon">chiamare il metodo della superclasse</font> si usa [[This and Super#Super|super]], questa andrà a trovare e chiamare lo stesso metodo ma <font style="color:salmon">della superclasse</font>.
  ![center](https://i.imgur.com/NxHYYz3.png)



