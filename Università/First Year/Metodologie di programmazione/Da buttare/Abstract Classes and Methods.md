#java #keyword 
____

Quando si crea una sottoclasse di una classe, la sottoclasse ottiene automaticamente tutti i campi e metodi della classe parente.

## Classi Abstract

Le classi con il keyword Abstract sono classi che non si possono istanziare, cioè non si possono creare istanze di classi astratte.

Queste sono utili quando si vogliono creare delle superclassi molto generici, dove non ha molto senso creare degli oggetti di queste superclassi.

Per esempio una superclasse "Animal" dovrebbe essere Abstract in quanto ha poco senso creare un oggetto animale.

Le classi Abstract servono a imporre e organizzare esattamente cosa ogni sottoclasse deve avere.

___

## Metodi Abstract

All'interno di classi astratte si può scegliere di creare dei metodi astratti.

I metodi astratti sono utili quando si crea un metodo in una superclasse astratta ma che non deve essere implementata in quanto dovrebbe avere funzionalità diverse per ogni sottoclasse.

Per esempio in una superclasse "Animal" il metodo makeNoise() dovrebbe essere Abstract in quanto ogni animale fare suoni differenti. 

Quando si definisce un metodo astratto la sintassi cambia:
- non si deve più specificare un corpo del metodo
- si mette un ; dopo la dichiarazione del metodo.
```java
public abstract class Animal{

	String name;
	int age;
	
	public abstract void makeNoise();
}
```
**RICORDA CHE**:
- se si definisce un metodo astratto, in tutte le sottoclassi deve per forza essere implementato questo metodo astratto.

___

Le classi Abstract possono sembrare molto simili a delle [[Interface (Interfacce)]]:
- impongono delle cose che ogni classe deve per forza implementare
- le interfacce vengono usate nelle classi attraverso la parola chiave "implements" simile al "extends" delle superclassi
```java
public interface thingsThatSomeClassesNeedToDo{
	int age = 1; // SONO STATIC E FINAL
	String name = "Pippo"; // SONO STATIC E FINAL

	public void parla(); // METODO DA IMPLEMENTARE
}
```
anche se ci sono differenze:
- si possono implementare infinite interfacce **ma** si può estendere **una sola classe**
- nelle interfacce **tutti** i campi devono essere inizializzati in quanto sono [[Static (keyword)]] e [[Final (keyword)]], quindi hanno un valore prefissato fisso per ogni oggetto. Questo non vale per le superclassi, che hanno campi propri per ogni oggetto.