#Superclass #java
___
# Upcasting

**RICORDA CHE**:
- In Java si può sempre considerare il tipo di un oggetto di una sottoclasse come il tipo della superclasse.
- Upcasting è **IMPLICITO E FUNZIONA SEMPRE**.

```java
public static void main(String[] args){
	Animal myAnimal = new Dog();
}
```
Questa cosa viene chiamata Upcasting. Nel codice il myAnimal è una variabile di tipo Animal (<font style="color:Indianred">Reference type</font>) che era inizialmente di tipo Dog, ma che è stato implicitamente upcastato ad Animal durante l'assegnazione.
(è ancora di tipo Dog)

Ora dato che myAnimal ha come reference type il tipo Animal, possiede tutti i metodi di Animal, ma non più quelli di Dog.

```java
public class Animal{

	public void makeNoise(){
		System.out.println("Animal sounds");
	} 
}

public class Dog extends Animal{

	public void makeNoise(){
		System.out.println("Woof woof");
	}
}

public static void doAnimalStuff(Animal animal){

	animal.makenoise();
}

public static void main(String[] args){
	Animal myAnimal = new Dog();
	doAnimalStuff(myAnimal); // STAMPA WOOF WOOF
}
```

Il metodo doAnimalStuff stampa "Woof woof" in quanto l'argomento passato, anche se ha come reference type Animal, è in realtà un Dog, quindi il metodo doAnimalStuff andrà a chiamare il metodo makeNoise() presente all'interno della classe Dog.

___

Quindi tutte le sottoclassi di Animal: cat, dog, bird, ...
hanno le loro implementazioni di makeNoise(), ed è possibile chiamare ogni singola implementazione grazie al Upcasting che rende ogni tipo di specie ad Animal, in modo tale che doAnimalStuff() andrà a chiamare il metodo in base al tipo in input.

Se non si usasse l'Upcasting si dovrebbe implementare un doAnimalStuff() per **OGNI TIPO DI SOTTOCLASSE**.

Il lato positivo è:
- si può creare un metodo che funziona per tutti i tipi delle sottoclassi, anche per quelli che non esistono ancora.

Una limitazione però è:
- dato che il metodo non sa con quale tipo sta lavorando, non si possono usare metodi che sono stati implementati **solo** nelle sottoclassi
- 
_____
# Downcasting

**RICORDA CHE**:
- Downcasting **NON È IMPLICITO, SI DEVE FARE ESPLICITAMENTE E SI POSSONO GENERARE ERRORI SE USATO MALE**

Si può fare Downcasting in Java quando si vuole cambiare dal tipo della superclasse a un tipo della sottoclasse.

Per esempio dal tipo Animal al tipo Dog.
```java
Dog myDog = (Dog)animal;
```

Facendo ciò Java tratterà myDog come una variabile di tipo Dog, permettendoci di usare i metodi della sottoclasse Dog.

Ora, se animal veramente è di tipo Dog, allora non uscirà nessun errore quando verrà usato un metodo della sottoclasse Dog.
Ma se animal **non** era veramente di tipo Dog, allora quando verrà usato un metodo della sottoclasse Dog, Java restituirà un Class Cast Expection.

Ma se si volesse comunque provare a Downcastare per usare un metodo di una particolare sottoclasse?:
si usa "instanceof"
```java
if (animal instanceof Dog) {
	Dog myDog = (Dog)animal;
	myDog.growl(); // METODO PRESENTE SOLO NELLA SOTTOCLASSE DOG
}
```
Quindi in questo codice, se animal è veramente di tipo Dog, allora si entrerà nel corpo dell'IF.