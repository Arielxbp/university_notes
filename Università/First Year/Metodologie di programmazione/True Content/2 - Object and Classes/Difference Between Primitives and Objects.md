___

- I <font style="color:salmon">valori</font> di [[Primitive Data Types|tipo primitivo]] sono <font style="color:salmon">diversi</font> dagli [[Classes|oggetti]].

La loro <font style="color:salmon">rappresentazione in memoria</font> è <font style="color:salmon">differente</font>:

- I <font style="color:salmon">valori primitivi</font> hanno la memoria allocata automaticamente a tempo di compilazione.

- Gli <font style="color:salmon">oggetti</font> hanno la memoria allocata durante l'esecuzione del programma, quando viene invocato il [[Classes#Constructors|costruttore]] con l'operatore <font style="color:salmon">new</font>.

# Comparing using Equals or ==
___
>[!info] 
>Per maggiori informazioni andare a [[Universal Superclass Object]].

- Quando si vogliono confrontare due variabili entrambi di <font style="color:salmon">tipo primitivo</font> è possibile usare l'[[Primitive Data Types#Comparing Operators|operatore di comparazione]]: $==$ 

- Quando si vogliono confrontare due variabili entrambi di <font style="color:salmon">tipi NON primitivi</font> è <font style="color:salmon">necessario</font> usare il metodo della [[Universal Superclass Object#equals Method|classe Object]]: equals()