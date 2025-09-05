#java 

Esistono diversi tipi di strutture dati:
- Collection
- Set (set di python)
- List (liste di python)
- Map (dizionario di python)
- Queue

Tutte sono delle sub dell'Iterable:
- Ereditano quindi tutti i metodi di Iterable.
![center](https://upload.wikimedia.org/wikipedia/commons/a/ab/Java.util.Collection_hierarchy.svg)
## Iterazione "interna" su una collezione

- Attraverso l'uso del metodo <font style="color:salmon">Iterable.forEach</font>:
  permette l'iterazione su qualsiasi collezione senza specificare come effettuare l'iterazione.
  
  Prende in input un <font style="color:salmon">Consumer</font>, che è un'interfaccia funzionale con un solo metodo.

## Modifica della collezione durante una iterazione

- <font style="color:salmon">Non è</font> possibile utilizzare metodi di modifica  durante un'iterazione:
```java
for (int k : l)
	if (k == x){
		l.remove(x);
	}
```

- <font style="color:salmon">Ma è</font> possibile utilizzare <font style="color:salmon">Iterator.remove</font>:
```java
Iterator<Integer> i = l.iterator();
while (i.hasNext())
	if (i.next() == x) i.remove();
```

# Liste
___

Sono basate sull'interfaccia <font style="color:salmon">List</font>, una sottointerfaccia di <font style="color:salmon">Collection</font> e di <font style="color:salmon">Iterable</font>.

Le classi liste sono:

- <font style="color:salmon">Array list</font>
  Implementa la lista attraverso un <font style="color:salmon">Array</font>.
  Ha una capacità iniziale di 10 elementi.
  
- <font style="color:salmon">Linked list</font>
  Implementa la lista attraverso <font style="color:salmon">elementi linkati</font>.

# Set
___

Sono basate su una sottointerfaccia di <font style="color:salmon">Collection</font> e di <font style="color:salmon">Iterable</font>.

Gli insiemi sono <font style="color:salmon">Collection</font> che contengono elementi <font style="color:salmon">tutti distinti</font>, cioè non esistono doppioni.

Le classi insiemi sono:

- <font style="color:salmon">HashSet</font>
  Memorizza gli elementi in una tabella di hash.
  L'ordine degli elementi non è assicurata da come si inseriscono.
  
  <font style="color:salmon">Esempio di codice</font>
```java
HashSet<String> nomi = new HashSet<String>();

nomi.add("Mario");
nomi.add("Luigi");
nomi.add("Mario");
nomi.add("Luigi");

System.out.println(nomi);
// Stampa [Mario, Luigi]
```

- <font style="color:salmon">TreeSet</font>

# Map (mappe)
___

Una <font style="color:salmon">Map</font> è un <font style="color:salmon">dizionario di Python</font>.

Mette in corrispondenza delle <font style="color:salmon">key</font> a dei <font style="color:salmon">value</font>.

Non può contenere <font style="color:salmon">chiavi duplicate</font>.

java.util.Map è un interfaccia implementata da:

- <font style="color:salmon">HashMap</font>
  Memorizza le coppie key-value in una tabella di hash

- <font style="color:salmon">TreeMap</font>
  Memorizza le coppie key-value in un albero, mantenendo un ordine sulle chiavi basato sulle prime lettere (ordine alfabetico)

- <font style="color:salmon">LinkedHashMap</font>
  Estende HashMap.
  Mantiene l'ordinamento di iterazione secondo gli inserimenti effettuati(simile alle liste).

<font style="color:salmon">Esempio di codice</font>:
```java
Se
```

## <font style="color:salmon">Metodi di java.util.Map (Java 8 >)</font>.

- forEach()
  Itera su ciascuna coppia key-value

- getOrDefault(key, defaultValue)
  Restituisce il value associato alla key o defaultValue se la chiave non è presente. 

- merge(key, value, BiFunction)
  Se la key non contiene già un valore, imposta il value specificato, altrimenti chiama una bifunzione che decide come mettere insieme il valore precendente con il valore dato in input.

- of()
  Statico.
  Crea una mappa <font style="color:salmon">immutabile</font> dei tipi e con i valori corrispondenti.

# <font style="color:salmon">Ordinamento</font>
___

## <font style="color:salmon">Ordinamento "naturale"</font>

- Usato da strutture dati come <font style="color:salmon">TreeSet </font> e <font style="color:salmon">TreeMap</font>.
- Queste strutture dati necessitano l'implementazione di un'interfaccia speciale, chiamata <font style="color:salmon">Comparable</font>.

## <font style="color:salmon">Ordinamento per altre strutture dati o diverso ordine</font>

- È sufficiente implementare un'interfaccia <font style="color:salmon">Comparator</font> e passarne un'istanza in input al costruttore delle strutture dati.

### <font style="color:salmon">Metodi dell'interfaccia Comparator</font>

- compare()
  Restituisce un Int.
  Compara due argomenti per ordinare.

- equals()
- Restituisce un Boolean.
  Indica se l'altro oggetto è "equal to" il comparato.

## <font style="color:salmon">Ordinamento inverso</font>

- TBD //

#

