#java 
# Classi (normali/top-level)
___

Le classi normali vengono dette top-level in quanto non sono contenute all'interno di altre classi.


# Classi annidate
___

Esistono due tipi di classi annidate:
- classi annidate non static (Inner Class / Classi interne):
Per creare un oggetto della classe interna bisogna prima istanziare un oggetto della classe esterna che la contiene.
Queste classi interne hanno un riferimento implicito all'oggetto della classe che la contiene.
Dalla classe interna si possono accedere a tutte le variabili e metodi della classe esterna.

- classi annidate [[Static (keyword)|Static]] (Nested Class)
Non richiede l'esistenza di un oggetto della classe esterna.
Non ha accesso implicito ai campi della classe esterna.
La classe annidata Static è visibile all'esterno.
Non possiede neanche un riferimento all'oggetto della classe esterna.
Il comportamento di una classe annidata Static è come se fosse una classe top-level all'interno di un'altra classe top-level.
Sono accessibili attraverso la seguente sintassi:
```java
new nomeClasseEsterna.nomeClasseAnnidataStatica()
```
Le classi nested sono utili in quanto:
- raggruppano classi logicamente vicine, cioè se una classe serve solo ad un'altra classe, tenerla dentro alla classe top-level è la scelta migliore.
- Migliora la funzionalità dell'incapsulamento, dato che una classe X nested in Y può accedere ai campi di Y anche se privati, mentre X non verrà mai vista da fuori Y.
- Codice più leggibile e facile da mantenere

# Classi anonime
___

- Le classi anonime sono delle classi **senza nome** che implementano un'interfaccia o che estendono una classe.

- Vengono utilizzate esclusivamente per creare un'unica istanza.

- La sintassi per una classe anonima è:
```java
TipoDaEstendere unicoRiferimentoAOggetto = new TipoDaEstendere(){
	// codice della classe anonima (implementazione dell'interfaccia
	// o estensione della classe)
};
```

- Il tipo da estendere può essere anche una classe astratta o un'interfaccia.

- Il keyword <font style="color:Indianred">this</font>, se usato con una classe anonima, si riferisce all'oggetto anonimo.