___

>[!info]
>[[Classes]], [[Inheritance]] e [[Abstract Methods]] sono strettamente collegati a questo argomento. 
>
>In [[Abstract Methods]] si usano queste <font style="color:springgreen">Abstract Classes</font>. 
>

- Una classe <font style="color:salmon">Abstract</font>, cioè "astratta", non può essere istanziata. Quindi la classe <font style="color:salmon">se è astratta</font>, allora <font style="color:salmon">non possono esistere</font> [[Classes#Objects|oggetti]] di quella classe.
  
>[!attention]
>Possono esistere oggetti di una classe Abstract tramite [[Upcasting and Downcasting|Upcasting]].

- Tipicamente queste classi vengono <font style="color:salmon">estese</font> da <font style="color:salmon">altre classi</font>.

- Sono utili quando si vogliono creare delle superclassi molto generiche, dove non ha molto senso creare degli oggetti di queste superclassi.

- Le classi Abstract servono a imporre e organizzare esattamente cosa ogni sottoclasse deve avere.

- Le <font style="color:springgreen">classi astratte</font> possono avere anche <font style="color:salmon">metodi NON abstract</font>.

# Abstract Classes and Interfaces
___

Le classi <font style="color:salmon">abstract</font> possono sembrare <font style="color:salmon">molto simili</font> alle [[Interfaces|interfacce]] in quanto:

- <font style="color:salmon">Impongono</font> delle funzioni che ogni classe <font style="color:salmon">deve</font> implementare.

- Le interfacce vengono usate nelle classi attraverso il [[Keywords|keyword]] <font style="color:salmon">implements</font>, simile al <font style="color:salmon">extends</font> delle [[Inheritance|superclassi]]. 

Però <font style="color:salmon">ci sono delle differenze</font>:

- Si possono implementare <font style="color:salmon">infinite</font> interfacce ma si può estendere <font style="color:salmon">una sola classe</font>.

- Nelle interfacce <font style="color:salmon">tutti i campi</font> devono essere inizializzati in quanto sono [[Keywords|static]] e [[Keywords|final]], quindi <font style="color:salmon">hanno un valore prefissato</font>, fisso per ogni oggetto.
  
  Questo <font style="color:salmon">non vale</font> per le superclassi, che <font style="color:salmon">hanno campi propri</font> per ogni oggetto.
