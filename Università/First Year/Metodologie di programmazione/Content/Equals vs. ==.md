#java 
___
In Java **TUTTI** i tipi non [[Primitive Types |primitivi]], incluso String, se assegnati a variabili, le variabili sono dei riferimenti alla memoria dove quell'oggetto sta.

In Java **TUTTI** i tipi [[Primitive Types |primitivi]] se assegnati a variabili, le variabili rappresentano il valore assegnato.

___
# Tipi primitivi
Quindi il == lo si usa quando si devono comparare due variabili di tipi primitivi
```java
int int1 = 1;
int int2 = 2;
if (int1 == int2){
	return true;
}
else{
	return false;
}
```
___
# Tipi non primitivi (String, Collections,...)
Per tutti gli altri tipi, quando si devono comparare due variabili che fanno riferimento a tipi non primitivi, si deve usare .equals()
```java
String string1 = "hello";
String string2 = "hello";
if (string1 == string2){
	return true; // NON FUNZIONA
}
if (string1.equals(string2)){
	return true; // FUNZIONA
}

```

___

# Tipi custom
Per i tipi custom, definiti dalle classi custom, se non viene implementato il metodo .equals() legato a quella particolare classe, viene usato quello di default di Java per gli object.

Quindi se si vuole usare .equals() su dei tipi custom, si deve implementare questo metodo all'interno della classe del tipo custom.

```java
public class Dog{

	private String name;
	private int age;

	public Dog(String name, int age){
		this.name = name;
		this.age = age;
	}

	// Implementazione del .equals()
	public boolean equals(Object obj){
		// TBD
	}	
}
```