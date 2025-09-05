___

- Tutte le classi in Java <font style="color:salmon">ereditano direttamente o indirettamente la </font> <font style="color:springgreen">classe Object</font>.

- Quando si definisce una classe:
  ![center](https://i.imgur.com/Ww3IZaZ.png)
  Questo è equivalente a scrivere:
  ![center](https://i.imgur.com/LQkmC4o.png)

# Methods of the Object Class
___

- https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html
![center](https://i.imgur.com/TksJBEL.png)

## toString Method

- <font style="color:springgreen">toString</font> è uno dei metodi che ogni classe eredita.

- <font style="color:salmon">Non prende argomenti</font> e restituisce una <font style="color:salmon">String</font>.

- <font style="color:salmon">È chiamato implicitamente</font> quando un oggetto deve essere convertito a <font style="color:salmon">String</font>, l'esempio più comune è quando si vuole <font style="color:salmon">stampare</font> con "System.out.println()".

## equals Method

- Il metodo <font style="color:springgreen">equals</font> viene invocato per <font style="color:salmon">confrontare</font> il contenuto di due oggetti.

>[!info] 
>Già introdotto in [[Difference Between Primitives and Objects]].

- La classe Object <font style="color:salmon">non conosce</font> il <font style="color:salmon">contenuto</font> delle sottoclassi.
  
  Per poter confrontare quindi due oggetti di <font style="color:salmon">tipo non primitivo</font> e <font style="color:salmon">non default di Java</font>, serve [[Overriding and Overloading#Overriding|overridare/sovrascrivere]] il metodo <font style="color:springgreen">equals</font>:
  
Comunemente per <font style="color:salmon">implementare come confrontare</font> due oggetti "custom" si usano i metodi:

- <font style="color:salmon">getClass</font>
- <font style="color:salmon">instanceOf</font>

Cosa dice la documentazione ufficiale su <font style="color:springgreen">equals</font>:
![center](https://i.imgur.com/SjAEqgO.png)

Cosa ne dice Joshua Block su quale metodo usare nella sovrascrittura di equals:
![center](https://i.imgur.com/YaN7oaH.png)

