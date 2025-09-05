#java 
___

Già introdotte nelle [[Abstract Classes and Methods|Classi astratte]].

Le interfacce specificano soltanto il comportamento degli oggetti.

Nelle interfacce non si possono implementare i metodi al suo interno.

Da Java 8 si possono implementare dei <font style="color:Indianred">metodi di default</font>all'interno delle interfacce tramite il keyword "default" oltre ai metodi statici.

Da Java 9 si possono inoltre definire metodi con keyword "private" nelle interfacce.

Se non esplicitamente scritti, tutti i metodi hanno implicitamente le keyword "public" e "abstract" nelle interfacce.
<font style="color:Indianred">test</font>
Se non esplicitamente scritti, tutti i campi hanno implicitamente le keyword "public", "[[Static (keyword)|static]]" e "[[Final (keyword)|final]]" nelle interfacce.

Questi metodi non hanno un corpo:
```java
public interface test{
	void method1();
	void method2();
}
```

<font style="color:Indianred">Si può estendere UNA SOLA superclasse, ma si possono implementare infinite interfacce</font>
```java
public class Item implements Colorable, Trasformable, Selectable{

	// METODI DI COLORABLE
	@Override
	public void color(){}
	@Override
	public void removeColor(){}

	// METODI DI SELECTABLE
	@Override
	public void select(){}
	@Override
	public void deselect(){}

	// METODI DI TRASFORMABLE
	@Override
	public void move(){}
	@Override
	public void rotate(){}
	@Override
	public void cut(){}
	@Override
	public void factorize(){}
}
```


Le interfacce risolvono il problema dell'ereditarietà multipla in Java.
___
Definisco l'interfaccia [[Iterator (Iteratore)|Iterable]]:
```java
public interface Iterable{

	boolean hasNext();
	Object next();
	void reset();
}
```
Definisco la classe MyIntegerArray che implementa l'interfaccia Iterable:
```java
public class MyIntegerArray implements Iterable{

	private Integer[] array;
	private int i = 0;

	public MyIntegerArray(Integer[] array){
		this.array = array;
	}

	@Override // METODO DALL'INTERFACCIA
	public boolean hasNext(){
		return i < array.length;
	}

	@Override // METODO DALL'INTERFACCIA
	public Object next(){
		return array[i++]
	}

	@Override // METODO DALL'INTERFACCIA
	public void reset(){
		k = 0;
	}
}
```
Testing delle funzionalità:
```java
public class Main{

	public static void main(String[] args){
		Iterable i1 = new MyIntegerArray(new Integer[] {10, 20, 30, 40});
		for (Iterable i : new Iterable[] {i1}){
			while(i.hasNext()){
				System.out.println(i.next());
			}
		}
	}

}
```
Non è la soluzione ideale per iterare su una collezione perché non permette di avere contatori individuali.

Usare l'interfaccia che Java ha già implementato attraverso l'import di java.util.Iterator<E\>
Questa interfaccia espone 3 metodi disponibili alla classe che ha implementato quest'interfaccia.
```java
public interface Iterator{

	boolean hasNext();
	E next(); // E è il tipo della collezione
	void remove();
}
```
I 3 metodi:
- il metodo hasNext() restituisce true se esiste ancora un successivo elemento nella collezione.
- il metodo next() restituisce l'elemento successivo
- il metodo remove() rimuove l'elemento corrente, ed è un operazione opzionale.
___
Quando si implementa un'interfaccia si viene forzati a:
- implementare **tutti** i metodi specificati da tale interfaccia.
o:
- dichiarare la classe che ha implementato tale interfaccia, con il keyword [[Abstract Classes and Methods|Abstract]].
___

Valgono le regole del [[Polymorphisma|Polimorfismo]] tra classi e interfacce, incluso l'[[Upcasting and Downcaasting]]

___
Quando una classe implementa due o più metodi uguali ma di diverse interfacce, per differenziarli si usa:
```java
nomeInterfaccia.super.nomeMetodo();
```

# Enum con interfacce

Le [[Enum (Enumeration)]] possono implementare interfacce per renderle estensibili.


# Metodo Clone()
Dalla interfaccia Cloneable si può usare il metodo clone(), questa serve per clonare un oggetto, anche se non effettua una copia di questa ma solamente il riferimento ad essa.

Dato che la copia dell'oggetto originale e il clone hanno diversi riferimenti:
```java
oggetto.clone() != oggetto // SEMPRE VERO
```

La copia ottenuta dall'uso di clone() è fatto campo per campo, cioè è una <font style="color:Indianred">shallow copy</font>. Quindi se l'oggetto ha solo campi di tipo primitivo funziona bene, se sono riferimenti allora non.

```java
public IntVector getCopy(){
	try{
		IntVector v = (IntVector)clone();
		v.list = (ArrayList<Integer>)list.clone();
		return v;
	}
	catch(CloneNotSupportedException e){
		return null;
	}
}
```

# Functional Interface(Interfaccia funzionale)

Le interfacce funzionali sono di tipo "SAM", ovvero Single Abstract Method. (per definizione)
Possono avere un unico metodo [[Abstract Classes and Methods#Metodi Abstract|astratto]].
