#java #keyword 
___
# Method overriding
Per "overridare" un metodo di una classe parente, bisogna implementare esattamente lo stesso metodo con le stesse keyword del metodo presente nel codice della classe parente.

```Java
public class Animal{
	public void eat(){
		System.out.println("munch munch")
	}
}

public class Dog extends Animal{
	public void eat(){
		System.out.println("chomp chomp")
	}
}
```

# Method overloading
Per overloading si intende quando in una classe si hanno due metodi con lo stesso nome ma che prendono parametri diversi.
```Java
public class cat extends Animal{
	public void eat(){
		System.out.println("chomp chomp")
	}
	public void eat(int numOfTimes){
		for (int i =0; i<numOfTimes; i++){
			System.out.println("nom nom nom")
		}
	}
}
```

