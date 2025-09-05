___

- I <font style="color:salmon">tipi generici</font> sono un <font style="color:salmon">modello di programmazione</font> che permette di definire con una sola dichiarazione, un intero <font style="color:salmon">inseme di metodi o di classi</font>.

- Si usano le <font style="color:salmon">parentesi angolari</font> per definire un tipo generico.

![center](https://i.imgur.com/kxWlVWV.png)

- Per convenzione i tipi generici sono chiamati con le lettere <font style="color:salmon">T</font>, <font style="color:salmon">S</font>. Nel caso in cui questi siano elementi di una [[Collections|Collection]] con la lettera **<font style="color:salmon">E</font>.

- I tipi generici sono differenti sulla base dei loro tipi:
 ![center](https://i.imgur.com/mSKP4nQ.png)
- L'[[Inheritance|ereditarietà]] tra i tipi generici <font style="color:salmon">non vale</font>.

- <font style="color:salmon">Però vale</font> l'ereditarietà tra le <font style="color:salmon">classi</font> che usano tipi generici:
  
  Per esempio:
```Java
List<Integer> list = new ArrayList<Integer>();
```
  
# Extending Generic Classes

- È possibile <font style="color:salmon">estendere</font> le classi generiche per creare classi più specifiche

# Comparable and Comparator Interface

- Queste due [[Functional Interface|interfacce funzionali]] sono <font style="color:salmon">generiche</font>.
![center](https://i.imgur.com/2Agasld.png)
![center](https://i.imgur.com/bMVSrXp.png)

# Most Common Use Case of <font style="color:salmon">Generics</font>

- L'utilizzo principale dei tipi generici è nelle [[Collections]].

# Generic Methods

- Per definire un metodo generico è necessario anteporre il <font style="color:salmon">tipo generico tra parentesi angolari al tipo di ritorno</font>.
  Quindi prima scrivere il generico e solo poi scrivere il tipo di ritorno.

## Generic Input of Generic Methods

- Gli argomenti di tipo generico in input a un metodo generico possono essere <font style="color:salmon">del tipo richiesto dal metodo</font> oppure <font style="color:salmon">un sottotipo del tipo richiesto dal metodo</font>.

- Tuttavia ciò non ci permette di aggiungere a delle liste inizializzate di tipo A oggetti di tipo B.
  
  Per esempio non si può aggiungere una pera a una lista di mele, creata a partire da una lista di <font style="color:salmon">tipi generici</font>, anche se il metodo usato per aggiungere questa pera alla lista ormai di mele, accetta in input il tipo frutto o un suo sottotipo (quindi anche pere).
```java
public static <T extends Frutto> void prendiFrutta(ArrayList<T> frutti)
{
	frutti.add(new Pera()); // Doesn't work!
}
```


continua a partire da pag 30////