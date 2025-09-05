___

- In Java è possibile scrivere <font style="color:salmon">classi all'interno di altre classi</font>.

- Le classi presenti all'interno sono chiamate <font style="color:springgreen">classi annidate</font>.

Possono essere <font style="color:salmon">static</font> o <font style="color:salmon">non-static</font>:

- Classi <font style="color:salmon">non-static</font> sono chiamate <font style="color:salmon">classi interne</font>. (inner class)

Servono a:

- <font style="color:salmon">raggruppamento logic delle classi</font>.
- <font style="color:salmon">Incapsulamento</font>.
- Codice più leggibile e più facile da mantenere.

# Inner Class
___

- Prima di poter creare un oggetto della classe interna è necessario istanziare la classe esterna che la contiene.

- Ciascuna classe interna ha un <font style="color:salmon">riferimento implicito</font> all'oggetto della classe che la contiene.

- Dalla classe interna è possibile accedere a <font style="color:salmon">tutte le variabili</font> e a <font style="color:salmon">tutti i metodi</font> della classe esterna.

- Come tutti i membri di una classe, le classi interne possono essere dichiarate <font style="color:salmon">public</font>, <font style="color:salmon">protected</font> o <font style="color:salmon">private</font>.

Per disambiguare casi di ambiguità come campi con lo stesso nome in entrambe le classi:

- Se dalla classe interna viene usato soltanto <font style="color:salmon">this</font>, allora si fa riferimento ai campi e ai metodi di quella classe.

- Per far riferimento ai campi e ai metodi della classe esterna si <font style="color:salmon">deve precedere al this il nome della classe esterna</font>.

# Nested Static Class
___

- Non serve l'esistenza di un oggetto della classe esterna per esistere.

- È come una classe top-level inserita all'interno di un'altra classe top-level.

- 