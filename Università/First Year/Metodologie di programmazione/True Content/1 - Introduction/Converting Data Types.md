___
>[!info]
>[[Autoboxing and Auto-Unboxing]] è strettamente collegato a questo argomento. 
>

- In Java esistono diversi modi per convertire il tipo dei dati.

# Explicit Conversion
___

- Una prima versione di conversione di dati è attraverso l'uso di <font style="color:salmon">dataTypeX.parseDataTypeX()</font>.
 ![center](https://i.imgur.com/ctKU5iD.png)
Altri metodi che fanno un lavoro simile sono:

- Math.round()
- Math.floor()
- Math.ceil()
- etc...

# Explicit Cast
___

- Per il Cast si bisogna <font style="color:salmon">mettere il tipo voluto tra le parentesi prima del valore della variabile</font>.
 ![center](https://i.imgur.com/LTpDHi6.png)
 - Convertendo in questo modo si vanno però a <font style="color:salmon">perdere informazioni</font> aggiuntive sul dato come nel caso da <font style="color:salmon">int a Double</font>.
 
# Implicit Cast
___

- Se il tipo di partenza è <font style="color:salmon">meno preciso</font>, Java lo converte <font style="color:salmon">in modo automatico</font> al tipo più preciso.
 ![center](https://i.imgur.com/JSbQsYa.png)
Il <font style="color:springgreen">Cast implicito</font> avviene <font style="color:salmon">in fase di assegnazione</font>:

- <font style="color:salmon">Byte</font>, <font style="color:salmon">Short</font> e <font style="color:salmon">Char</font> possono essere promossi a <font style="color:salmon">Int</font>.

- <font style="color:salmon">Int</font> può essere promosso a <font style="color:salmon">Long</font>.

- <font style="color:salmon">Float</font> può essere promosso a <font style="color:salmon">Double</font>.

O avviene in fase di <font style="color:salmon">calcolo di un'espressione</font>:

- Se uno dei due operandi è <font style="color:salmon">Double</font>, l'intera espressione è promossa a <font style="color:salmon">Double</font>.
