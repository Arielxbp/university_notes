___

- Spesso è utile definire delle <font style="color:springgreen">enumerazioni</font>. Questi vengono usati quando <font style="color:salmon">c'è qualcosa all'interno del codice che usa un set predefinito di valori che non cambiano</font>.

- Le <font style="color:salmon">costanti enumerative</font> sono implicitamente con visibilità [[Keywords#Static|Static]].

- Per convezione queste costanti si scrivono <font style="color:salmon">in maiuscolo</font>.

- Non si possono creare altre variabili di una classe Enum all'interno di altre classi.

- Una enumerazione ha <font style="color:salmon">tante istanze</font> quante sono le <font style="color:salmon">costanti enumerative</font> al suo interno, e non è possibile costruirne altre di <font style="color:salmon">istanze</font>.

## Enum Default Methods

Le classi enumerative estendono la classe <font style="color:salmon">Enum</font>, da cui ereditano i metodi:

- <font style="color:salmon">toString</font>: questa restituisce il nome della costante.

- <font style="color:salmon">clone</font>: restituisce l'oggetto enumerativo stesso <font style="color:salmon">senza farne una copia</font>.
  (dato che non è possibile fare copie, visto che sono costanti)

<font style="color:salmon">Attenzione</font>: La classe <font style="color:salmon">Enum</font> a sua volta estende la classe <font style="color:salmon">Object</font>, per cui il metodo <font style="color:salmon">equals</font> restituisce <font style="color:salmon">true</font> solo se le costanti enumerative <font style="color:salmon">sono identiche</font>.

## Enum components

- Quando si definiscono dei <font style="color:salmon">campi per le costanti di un Enum</font>, queste si devono <font style="color:salmon">inserire nelle parentesi di ognuna costante</font>.
  
- Questi campi <font style="color:salmon">devono essere</font> [[Keywords#Final|final]] in quanto <font style="color:salmon">non devono essere modificati</font> attraverso il costruttore.

- <font style="color:salmon">Inoltre</font> si deve creare un [[Classes#Constructors|costruttore]] però <font style="color:salmon">senza</font> [[Keywords|keywords]].
 
- Un tipo <font style="color:salmon">Enum</font> viene dichiarato mediante la sintassi:
  ![center](https://i.imgur.com/Xjz25C5.png)

Come tutte le altre [[Classes|classi]], la dichiarazione di una <font style="color:springgreen">enumerazione</font> può contenere <font style="color:salmon">altre componenti tradizionali</font>:

- <font style="color:salmon">Costruttori</font>
- <font style="color:salmon">Campi</font>
- <font style="color:salmon">Metodi</font>
  ![center](https://i.imgur.com/P4UFHre.png)
- <font style="color:salmon">Attenzione</font>: il costruttore <font style="color:salmon">NON FUNZIONA</font>, bisogna solamente scriverlo se le costanti hanno dei campi.


Per ogni <font style="color:springgreen">enumerazione</font>, il compilatore in automatico genera i metodi <font style="color:salmon">Static</font>:

- <font style="color:salmon">values()</font>
- <font style="color:salmon">valuesOf()</font>
 ![center](https://i.imgur.com/1YKmY5F.png)

