#java #keyword
___
La parola chiave **Final** può essere usata in 3 modi:

1) Come parola chiave per una classe
```java
public final class Animal{
	//
}
```
Se viene usato in questo modo, la classe con la parola chiave final **NON** può più essere extendato da nessuna classe, ovvero non può più avere sottoclassi.


2) Come parola chiave per un metodo
```java
public class Animal{
	public final void eat(){
		System.out.println("munch munch")
	}
}

public class Dog extends Animal{
	public void eat(){
		System.out.println("nom nom") // NON FUNZIONA
	}
}
```
In questo caso la parola chiave final viene usato sul metodo eat() in modo tale da renderlo non overridable, cioè anche se la classe Dog estende Animal, Dog **non potrà cambiare l'implementazione** del metodo eat() tramite overriding perché nella classe Animal il metodo eat() è stato definito **final**

3) Come parola chiave per una variabile
```java
public class Math{

	public static final double PI = 3.14159;
	public static final double E = 2.7182818284;

}
```
In questo caso la parola chiave final viene usata per rendere delle variabili in costanti.

Se si usa final per delle variabili allora quelle variabili possono essere assegnate **UNA SOLA VOLTA** e dopodiché non si possono più cambiare.
Questo vale anche per tipi non primitivi.

Esempio dove myDog viene reso final
```java
public class Dog{
	private String name;
	private int age;
	public Dog(String name, int age){
		this.name = name;
		this.age = age;
	}
}

public class Main{
	public static void main(String[] args){
	final Dog myDog = new Dog("Cane",2);
	myDog = newDog("Cane2", 1); // NON FUNZIONA
	}
}
```
