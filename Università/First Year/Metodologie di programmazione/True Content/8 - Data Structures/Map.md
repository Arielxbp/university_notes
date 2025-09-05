___

- <font style="color:salmon">È un dizionario di Python</font>.

- Una <font style="color:springgreen">mappa</font> mette in corrispondenza <font style="color:salmon">key</font> e <font style="color:salmon">value</font>.

- <font style="color:salmon">NON</font> può contenere <font style="color:salmon">chiavi duplicate</font>.

- Le classi Map, <font style="color:salmon">HashMap</font>, <font style="color:salmon">TreeMap</font> e <font style="color:salmon">LinkedHashMap</font>, implementano l'interfaccia <font style="color:salmon">java.util.map</font>.

>[!info] 
><font style="color:salmon">HashMap</font> memorizza le coppie in una tabella di hash.
>
><font style="color:salmon">TreeMap</font> memorizza le coppie in un albero mantenendo un ordine sulle chiavi.
>
><font style="color:salmon">LinkedHashMap</font> estende <font style="color:salmon">HashMap</font> e mantiene l'ordinamento di iterazione secondo gli inserimenti effettuati.

## Key and Values

- È possibile ottenere l'insieme delle chiavi di una mappa mediante il metodo <font style="color:salmon">keySet</font>.

- È possibile ottenere l'elenco dei valori mediante il metodo <font style="color:salmon">values</font> (con ripetizione!)

- È possibile ottenere l'insieme delle coppie <font style="color:salmon">key/values</font> mediante il metodo <font style="color:salmon">entrySet</font>.

# Order of the elements in Maps

- <font style="color:salmon">HashMap</font>: tutto casuale

- <font style="color:salmon">TreeMap</font>: ordine naturale delle chiavi, cioè ordine alfabetico

- <font style="color:salmon">LinkedHashMap</font>: ordine di inserimento delle chiavi.

# Some Methods for Maps

- <font style="color:salmon">forEach</font>(BiConsumer): itera su ciascuna coppia <font style="color:salmon">key/value</font>.

- <font style="color:salmon">getOrDefault</font>(key, defaultValue): restituisce il valore associato alla chiave o defaultValue se la chiave non è presente.

- <font style="color:salmon">of</font>(key, value, key, value,...., key, value): <font style="color:salmon">statico</font>, crea una mappa immutabile dei tipi e con i valori corrispondenti.

