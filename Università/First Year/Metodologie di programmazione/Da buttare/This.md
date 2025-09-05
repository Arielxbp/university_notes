#overloading #keyword #java
___
La parola chiave **This** può essere usata in 2 modi: Entrambi all'interno di [[Constructors (Costruttori)]]

1) Come keyword che specifica a Java che ci si sta riferendo al campo di un oggetto sulla quale il metodo è stato chiamato.
```java
public class Dog{
	private String name;
	private int age;

	public Dog(String name, int age){  // CONSTRUCTOR 
		this.name = name;
		this.age = age;
	}

	public setName(String name){  // SETTER
		this.name = name;
	}
}
```

___

2) Come keyword all'interno di un costruttore che invoca un altro costruttore
```java
public class Dog{
	private String name;
	private int age;

	public Dog(){
		this("name", 0);
	}

	public Dog(String name, int age){  // CONSTRUCTOR 
		this.name = name;
		this.age = age;
	}
}
```
Quando si usa this() come keyword che invoca un altro costruttore, Java automaticamente va a cercare a quale costruttore deve delegare la creazione dell'istanza guardando ai tipi degli input forniti all'interno del this().

Generalmente this() si usa per avere più costruttori (overloading) che magari non chiedono in input tutti i campi dell'oggetto.

**RICORDA CHE**:
la riga di codice dove viene implementata this() **deve** essere la **prima** riga del costruttore
```java
public class Dog{
	private String name;
	private int age;

	public Dog(){
		System.out.println("created new dog!");
		this("Fuffi", 0); // NON FUNZIONA, NON STA ALLA PRIMA RIGA
	}
	public Dog(String name, int age){  // CONSTRUCTOR 
		this.name = name;
		this.age = age;
	}
}
```