___

# Stream

- Una stream è una sequenza di elementi sulla quale si possono applicare operazioni che servono per elaborare questi dati.
- Gli stream fanno parte della programmazione funzionale.

- Gli stream non modificano la collezione originale durante le operazioni eseguite su di essa
- Una volta creato una stream a partire da una collection, si possono effettuare operazioni che sono intermedie o terminali.
- Le operazioni intermedie alla fine restituiscono un altro stream con la quale lavorare
- Le operazioni terminali restituiscono il tipo atteso dell'operazione eseguita
- Una volta che uno stream è stato consumato(tramite operazione terminale), esso non può essere riutilizzato
- Le operazioni intermedie sono simili a un builder pattern e servono a <font style="color:salmon">dichiarare</font> le operazioni che devono essere effettuate
- Le operazioni intermedie non vengono eseguite subito, ma solamente quando viene eseguito una operazione terminale, quindi quando bisognare terminare lo stream
- Gli stream adottano uno stile dichiarativo, dove dobbiamo solo dichiarare quali operazioni devono essere effettuate per elaborare il flusso di dati.
- Diverso dallo stile imperativo, dove l'utente deve esplicitamente scrivere le istruzioni da far eseguire alla macchina, passo dopo passo. (L'utente decide il come)
```Java
public Map<Ex2_EnumNomeIngrediente, List<Double>> getHashMappaIngredientiQuantitaPerTipologiaRicette(Ex2_Tipologia tipologia) {

return listaRicette.stream()
// filtro le ricette lasciando solo quelle della specifica tipologia dato in input 
.filter(ricetta -> ricetta.getTipologia().equals(tipologia))
// per ogni ricetta rimasta, estraggo la lista degli ingredienti e li dispongo in modo da avere una singola lista sulla quale uso un stream
// (come se per ogni ricetta ho una lista dei suoi ingredienti, se faccio uno stream allora avro uno stream di liste di ingredienti. Invece se flatmappo allora avro' una stream di una singola lista di tutti gli ingredienti)
.flatMap(ricetta -> ricetta.getIngredienti().stream())
// colleziono nella map da restituire avendo per chiave il nome dell'ingrediente
// specifico che si deve usare una hashtable per l'implementazione della mappa da restituire
.collect(Collectors.groupingBy(ingrediente -> ingrediente.getNome(),() -> new Hashtable<>(),
// colleziono nella map da restituire avendo per valore una lista delle singole quantita' dell'ingrediente di ogni ricetta che creo attraverso il tolist
Collectors.mapping(ingrediente -> ingrediente.getQuantità(), Collectors.toList())));

}
```
- Uno stream è un paradigma di dichiarazione di tipo dichiarativo che permette la composizione di operazioni intermedie(building block) che servono per elaborare un flusso di dati, inoltre è anche parallelizzabile(usa tutti i core della cpu).
- Gli stream sono un meccanismo che ci permettono di effettuare operazioni su una sequenza di elementi
- Gli stream sono dei flussi di dati sulla quale si possono effettuare operazioni 

### Stateless e Stateful
- Esistono due tipi di operazioni intermedie: <font style="color:salmon">Stateless</font> e <font style="color:salmon">Stateful</font>.
- Le operazioni intermedie <font style="color:salmon">Stateless</font> sono operazioni che quando vengono eseguite tramite il <font style="color:salmon">lazy behaviour</font>, possono essere effettuate in modo libero in quanto l'operazione non impatta sui dati.
  Non hanno nessun impatto sul ridefinire un ordinamento di esecuzione delle operazioni intermedie.
- Le operazioni intermedie <font style="color:salmon">Stateful</font> sono operazioni che quando vengono eseguite tramite il <font style="color:salmon">lazy behaviour</font>, hanno un impatto su come deve essere eseguita la sequenza delle operazioni intermedie

## Lambda

- Fa parte del paradigma chiamato programmazione funzionale
- Manca il nome della funzione e la sua visibilità
- Usati per implementare l'unico metodo astratto delle SAM come per quelle built-in come predicate, function, supplier o consumer

## Interfacce built-in (predicate, function, supplier, consumer)

- Predicate (prende in input e restituisce un booleano)
  p -> p < 1;
  String::isEmpty

- Function (prende in input e restituisce un output)
  p -> p.multiply()
  String::valueOf
  p -> String.valueOf(p);

- Supplier (non prende in input e restituisce un output)
  Player::new;
  () -> new HashTable<>();
  () -> new Player();

- Consumer (prende in input e non restituisce un output)
  System.out::println
  p -> System.out.println(p)
## Generici

- [[Generics]]

- I tipi generici sono un modello di programmazione che permette di definire con una sola dichiarazione, un intero <font style="color:salmon">inseme di metodi o di classi</font>. 

- L'utilizzo principale dei generici è nelle collezioni

- È possibile <font style="color:salmon">estendere</font> i metodi/classi generici per creare metodi/classi più specifici

- T extends Frutto -> indica che T può essere di tipo frutto o un sottofrutto come mela

- ? extends T -> indica che prende in input un T o un sottotipo di T (<font style="color:salmon">Covarianza</font>)

- ? super T -> indica che prende in input un T o un supertipo di T  (<font style="color:salmon">Controvarianza</font>)

## Abstract Classes

- [[Abstract Classes]]

- Una classe astratta non può essere istanziata. Quindi la classe <font style="color:salmon">se è astratta</font>, allora <font style="color:salmon">non possono esistere</font> [[Classes#Objects|oggetti]] di quella classe.
  
- Possono esistere oggetti di una classe Abstract tramite [[Upcasting and Downcasting|Upcasting]].

- Queste classi vengono <font style="color:salmon">estese</font> da <font style="color:salmon">altre classi</font>.
- Sono utili quando si vogliono creare delle superclassi molto generiche, dove non ha molto senso creare degli oggetti di queste superclassi.

- Le classi astratte servono a imporre e organizzare esattamente cosa ogni sottoclasse deve avere.

- Le <font style="color:springgreen">classi astratte</font> possono avere anche <font style="color:salmon">metodi NON abstract</font>.

## Ereditarietà

- [[Inheritance]]
- L'ereditarietà è un concetto fondamentale della programmazione ad oggetti che permette di stabilire delle relazioni gerarchiche tra varie classi.
- Una classe se viene estesa da un'altra diventa una superclasse e la classe che estende ottiene tutti i campi e metodi della superclasse
- Una subclasse può overridare i metodi della superclasse dalla quale ha ottenuto il metodo
- Il costruttore della sottoclasse richiama quello della superclasse, se non viene esplicitamente chiamato allora java proverà a chiamare implicitamente il costruttore vuoto della supeclasse e se non presente si andrà incontro a un errore.

- L'ereditarietà viene implementata in quanto aumenta la riusabilità del codice.
- Organizza e struttura le classi in modo preciso attraverso una gerarchia
- Polimorfismo, fa in modo che oggetti di classi differenti possano essere trattati come oggetti della stessa supeclasse, migliorando la flessibilità del codice e la estendibilità.

## Polimorfismo

- [[Polymorphism]]
- Il polimorfismo è uno dei concetti fondamentali della programmazione orientata ad oggetti.
- Attraverso questo concetto, una variabile che ha il tipo della superclasse può contenere un riferimento a un oggetto che ha il tipo di una qualsiasi delle sue sottoclassi
- La selezione del metodo da chiamare <font style="color:salmon">avviene in base all'effettivo tipo</font> dell'oggetto riferito dalla variabile.
- - Il <font style="color:springgreen">polimorfismo</font> implementa il <font style="color:salmon">binding dinamico</font>, in quanto <font style="color:salmon">l'associazione</font> tra una variabile riferimento e il metodo viene stabilito <font style="color:salmon">a tempo di esecuzione</font>.
## Modello di memoria

- Java non ha puntatori ma solo riferimenti a oggetti in memoria nella heap

- Quando viene creato un oggetto con new , viene allocata della memoria per quell'oggetto nella heap
- Una variabile di riferimento viene creata per salvarsi il riferimento all'oggetto nella heap
- Per interagire con l'oggetto si usa la variabile di riferimento
- Quando l'oggetto non ha più riferimenti a esso, il garbage collector si riprende la memoria occupata 

## Dichiarazione implicita dei metodi nelle interfacce

The rules for _implicit_ modifiers do not change. Implicit modifiers are used when no other modifiers are specified. `abstract` is implied when neither `static` nor `default` has been specified. And all methods are always `public` whether implicit or explicit. Note that `interface` fields were always implicitly `public` `static`. This doesn’t change too.

- Quando si definiscono dei metodi in una interfaccia, se non vengono esplicitati la tipologia e la visibilità, allora sono implicitamente public e abstract.
- Se si esplicita il static o default allora ok.

## Binding statico

- Occurs at compile time.
- The compiler determines which method to call based on the declared type of the reference variable.
- Method overloading is an example of static binding.
```Java
class Animal {
    void makeSound() {
        System.out.println("Generic animal sound");
    }
}
class Dog extends Animal {
    @Override // Overloading
    void makeSound(String sound) {
        System.out.println("Woof!"+sound);
    }
}

In this example, even though `dog` is a `Dog` object, the compiler resolves the `makeSound()` call to the `Animal` class's method because the reference variable `dog` is declared as type `Animal`.
```

## Binding dinamico

- Occurs at runtime.
- The JVM determines which method to call based on the actual object type at runtime, not just the declared type.
- Method overriding is an example of dynamic binding.

So, the fundamental difference between static and dynamic binding in Java is that **the former occurs early, at compile time, based on the type of the reference variable, and the latter occurs later, at runtime, using concrete objects**.