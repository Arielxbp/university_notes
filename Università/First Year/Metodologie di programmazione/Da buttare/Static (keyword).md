#keyword #java
___
La parola chiave **Static** può essere usata in 2 modi:
- Come parola chiave di un metodo
- Come parola chiave di una variabile
```java
public class Cat{
	private static int catCounter = 0;

	public Cat(){ // METODO COSTRUTTORE
		catCounter++;
	}
}
```
In questo esempio Static viene usato come parola chiave per una variabile catCounter che tiene traccia di quanti gatti sono stati creati attraverso il costruttore.

Per accedere a tale variabile che tiene traccia è fortemente consigliato creare un metodo static che restituisce tale conto.
```java
public class Cat{
	private static int catCounter = 0;

	public Cat(){ // METODO COSTRUTTORE
		catCounter++;
	}

	public static int getCatCounter(){
		return catCounter
	}
}
```

___

# La differenza tra static e non-static

I campi e metodi non-static **NON POSSONO MAI** essere chiamati da oggetti della classe (**FUNZIONA MA NON È CONSIGLIATO**)

In quanto ha poco senso ottenere un campo static tramite un istanza della classe che ha un campo static.
Questo perché è ambiguo chiamare il metodo static su un oggetto, cioè da un gatto sto chiedendo il numero di gatti creati dalla classe.
Invece è meglio chiedere dalla classe il numero di gatti creati dalla classe.

```java
public class Cat{
	private static int catCounter = 0;

	public Cat(){ // METODO COSTRUTTORE
		catCounter++;
	}

	public static int getCatCounter(){
		return catCounter
	}
}
public class Main{
	public static void main(String[] args){

	Cat myCat = new Cat()

	myCat.getCatCounter() // NON CONSIGLIATO

	Cat.getCatCounter() // FUNZIONA
	
	}
}
```

___

I metodi static **NON POSSONO MAI** avere al loro interno dei riferimenti a **campi non-static**.

In quanto non ha senso ottenere un campo di un oggetto su una classe:
Non ha senso chiedere per esempio il campo name di una classe quando questo campo name è riferito a un singolo gatto

```java
public class Cat{
	private static int catCounter = 0;
	private String name;

	public Cat(){ // METODO COSTRUTTORE
		catCounter++;
	}

	public static int getCatCounter(){
		System.out.println(name); // NON FUNZIONA
		return catCounter
	}
}
```

___

# Static per definire costanti

Si usa la parola chiave static anche per definire costanti di classe: ovvero delle costanti che tutte le istanze hanno.

Queste (campi) costanti possono essere chiamate sia da instanze/oggetti che dalla classe.

Per esempio tutti i gatti hanno 9 vite all'inizio.
```java
public class Cat{
	public static final int MAX_LIVES = 9; // COSTANTE STATIC
	private static int catCounter = 0;
	int remainingLives;
	
	public Cat(){ // METODO COSTRUTTORE
		catCounter++;
		remainingLives = MAX_LIVES;
	}
	
	public static int getCatCounter(){
		System.out.println(name); // NON FUNZIONA
		return catCounter
	}
}
```