#keyword #Superclass #java
___
La parola chiave **Super** può essere usata in 2 modi:

1) Come keyword all'interno di un metodo che è stato ereditato e overridato.
```java
public class Animal{

	protected String name;
	protected int age;

	public Animal(){
	}

	public void makeNoise(){
	System.out.println("Noise");
	}
}

public class Dog extends Animal{

	protected String breed;

	@Override
	public void makeNoise(){ // METODO DELLA SOTTOCLASSE
	super.makeNoise() // METODO DELLA SUPERCLASSE
	System.out.println("Woof woof");
	}
}
```

In questo caso il keyword **Super** viene usato per richiamare il metodo della superclasse anche se è stato overridato.

Solitamente lo si usa all'interno del metodo overridato ma lo si può chiamare anche all'interno di altri metodi della classe figlio, anche se non sono lo stesso metodo.

___

**NON** si può usare super in questo modo al di fuori di sottoclassi di superclassi.

Per esempio se si vuole usare il metodo makeNoise() della superclasse Animal tramite un istanza della classe Dog si potrebbe pensare di fare così:
```java
Dog myDog = new Dog();
myDog.super.makeNoise(); // NON FUNZIONA
```
Questo codice non funziona in quanto il keyword Super si può usare solo all'interno di una classe per riferirsi alla sua superclasse.

**ATTENZIONE**: se si vuole usare un metodo della superclasse ma che ha visibilità Private, non si può usare super per richiamarlo anche se è dalla sottoclasse.
Se il metodo è Protected o Public invece è possibile.

____

2) Come keyword per richiamare il costruttore della superclasse per creare l'oggetto.
```java
public class Animal{

	protected String name;
	protected int age;

	public Animal(String name, int age){
		this.name = name;
		this.age = age;
	}
}

public class Dog extends Animal{

	protected String breed;

	public Dog(String name, int age, String breed){
		super(name,age); // USO DEL SUPER NEL COSTRUTTORE
		this.breed = breed;
	}
}
```
In questo codice il keyword Super viene usato per chiamare il costruttore della superclasse Animal, che per funzionare, ha bisogno di due argomenti, name e age, che gli vengono forniti tramite il super presente nel costruttore della sottoclasse.
In questo modo si riusa il codice non rendendolo ridondante.
Facendo così nel costruttore della sottoclasse si dovrà solo pensare a implementare i campi della sottoclasse e non di tutti quelli presenti nelle superclassi.

**ATTENZIONE**:
Se nel costruttore della sottoclasse non c'è il keyword super() che chiama il costruttore della superclasse, Java implicitamente chiamerà nel costruttore della sottoclasse il costruttore **VUOTO** della superclasse.

Se nella superclasse non esiste un costruttore vuoto allora all'interno del costruttore della sottoclasse verra segnalato un errore.
```java
public class Animal{

	protected String name;
	protected int age;

	public Animal(String name, int age){
		this.name = name;
		this.age = age;
	}

}

public class Dog extends Animal{

	protected String breed;

	public Dog(String name, int age, String breed){
	
		super(); // IMPLICITO SE NON SCRITTO
		// SE NON ESISTE IL COSTRUTTORE Animal(){} DA ERRORE
	
		this.breed = breed;
	}
}
```
![[Pasted image 20240331172354.png]]

**ATTENZIONE**:
Quando si usa super nel costruttore, fare attenzione a quali argomenti si danno, se nel super vengono forniti dati di tipo diverso o in più dai tipi che servono al costruttore della superclasse, questo non funzionerà in quanto non esiste un costruttore nella superclasse che ha quei tipi.
Esempio:
```java
public class Animal{

	protected String name;
	protected int age;

	public Animal(String name, int age){
		this.name = name;
		this.age = age;
	}

}

public class Dog extends Animal{

	protected String breed;

	public Dog(String name, int age, String breed){
		super(name,age, "Alto"); // NON FUNZIONA 
		this.breed = breed;
	}
}
```
L'errore sarebbe: la superclasse non possiede nessun costruttore che prende in input (string, int, string).

**RICORDA CHE**:
- la riga di codice dove viene implementata super() **deve** essere la **prima** riga del costruttore della sottoclasse.
- super() deve essere scritto solo nel metodo costruttore della sottoclasse.
- 