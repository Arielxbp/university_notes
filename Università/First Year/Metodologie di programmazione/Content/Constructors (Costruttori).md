#java
___
Un costruttore è un particolare tipo di metodo che serve per creare nuovi oggetti di quella classe.

```Java
public class Dog{
	private String name;
	private int age;
	public Dog(){ // Sottinteso da Java
	}             // 
}
```

Il metodo costruttore non ha nessun tipo di ritorno e viene scritto sempre con lo stesso nome della classe.
Java crea di default un metodo costruttore di una classe quando non viene specificatamente scritto, questo costruttore però non può prendere nessun parametro in ingresso e serve solamente a creare un'istanza della classe "vuota", ovvero con i parametri della classe non inizializzati.
## Attenzione
Solo se non viene creato nessun metodo costruttore allora Java provvede a creare in background un costruttore vuoto.

Se viene creato un costruttore allora Java **NON** provvederà a creare in back un costruttore vuoto. Questo vuol dire che non si potrà più creare un'istanza attraverso il costruttore vuoto perché Java non l'ha creato.

__________

Se si danno in input al costruttore dei parametri allora viene creato un'istanza della classe con i parametri definiti precedentemente nella classe.
```Java
public class Dog{
	private String name;
	private int age;
	public Dog(String name, int age){
		this.name = name;
		this.age = age
	}
}
```

_____

# Classe senza costruttore

Per avere una classe senza costruttore, per esempio in una classe dove si definiscono solamente delle costanti da usare in altre classi, quello che si deve fare è creare un costruttore custom ma dare visibilità protetta invece che pubblica.
```Java
public class Constants{
	private Constants(){ // Costruttore custom
	}                    // con visibilità private
	public static final int MONTHS_IN_A_YEAR = 12;
	public static final int DAYS_IN_A_WEEK = 7;
}
```