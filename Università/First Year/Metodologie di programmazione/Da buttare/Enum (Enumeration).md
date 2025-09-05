#java #keyword
___
Gli Enum vengono usati quando c'è qualcosa all'interno del codice che ha un set predefinito di valori che non cambiano.

Per esempio il movimento direzionale delle entità in un gioco.

Per convezione le costanti di un Enum si scrivono tutte in maiuscolo

Tutte le classi Enum estendono la classe java.lang.enum automaticamente (non c'è bisogno di scriverlo esplicitamente)

Esempio con i giorni della settimana:
```Java
public enum DaysOfTheWeek{
	SUNDAY,
	MONDAY,
	TUESDAY,
	WEDNESDAY,
	THURSDAY,
	FRIDAY,
	SATURDAY;
}
```

Queste costanti possono essere usate in altre classi ma non si possono creare altre variabili di una classe Enum all'interno di altre classi.

```Java
public test{
	public static void main(String[] args){
		DaysOfTheWeek newDay = new DaysOfTheWeek();
	}   //NON FUNZIONA
}
```

Non funziona il costruttore della classe Enum "DaysOfTheWeek" in quanto **una classe Enum è progettata per essere un set predefinito di valori da usare**.

___

Possiamo definire dei campi all'interno di una classe Enum
```Java
public enum Cereals{
	MIEL_POPS("Buono", 2.90)
	CHOCO_KRAVE("Ci sta", 3.19)
	SOTTOMARCA_FRUTTA("Senza sapore", 1.50)

	final String gusto;
	final double prezzo;

	Cereals (String gusto, double prezzo){
		this.gusto = gusto;
		this.prezzo = prezzo;
	}
}
```

Quando si definiscono dei campi per le costanti di un Enum, queste si devono inserire nelle parentesi di ognuna costante.

Questi campi **devono essere** con la parola chiave **final** in quanto non devono essere modificati attraverso il costruttore.

Inoltre si deve creare un costruttore senza parole chiave(?) dove si inseriscono i campi.

Per usare queste costanti si scrive: nomeDellaClasseEnum.COSTANTE
```Java
public class test{
	public static void main(String[] args){

		DaysOfTheWeek day = DaysOfTheWeek.THURSDAY;
		if (day == DaysOfTheWeek.THURSDAY){
			System.out.println("è quasi venerdì!")
		}

		System.out.println(Cereals.MIEL_POPS.gusto);
		// stampa "Buono"
	}
}
```