___

- Le classi sono codici di un programma che descrivono un particolare tipo di oggetti. 

Una <font style="color:springgreen">classe</font> è costituita da:

- <font style="color:salmon">Campi</font> (stato degli oggetti)
- <font style="color:salmon">Metodi</font> (comportamento degli oggetti)

Un <font style="color:salmon">oggetto</font> è un'istanza di una classe. Viene creato un nuovo oggetto ogni volta che viene chiamato il [[Classes#Constructors|costruttore]] della classe.

# Fields
___

- I campi sono tipicamente ad <font style="color:salmon">accesso privato</font>.

- Se viene usato il [[Keywords|keyword Static]] sul campo, questa indica che quel specifico campo è <font style="color:salmon">condiviso con tutti gli altri campi</font>.

- Se viene usato il [[Keywords|keyword Final]] sul campo, questa indica che il campo è una <font style="color:salmon">costante</font>.

# Methods
___

- I metodi sono tipicamente ad <font style="color:salmon">accesso pubblico</font>.

- Un metodo può <font style="color:salmon">restituire</font> un valore al chiamante.

- Se viene usato il [[Keywords|keyword Void]] sul metodo, questa indica che il metodo <font style="color:salmon">non restituisce alcun valore</font>.

- Il <font style="color:salmon">numero</font> e i <font style="color:salmon">tipi</font> degli argomenti passati a un metodo deve <font style="color:salmon">coincidere</font> con gli argomenti richiesti dal metodo.

>[!important] 
>Ricorda che si può riferire a un metodo attraverso la sintassi:
>ClasseDelMetodo :: metodo;
>Il metodo anche se è d'istanza funziona in quanto il compilatore sovraccarica il metodo, aggiungendo il riferimento a un oggetto istanza della classe in questione,
>e richiama il metodo originale su quel riferimento.
>

## Constructors

- Un <font style="color:springgreen">costruttore</font> è un <font style="color:salmon">metodo</font> che serve per creare gli oggetti di una <font style="color:salmon">classe</font>.

- Possiedono <font style="color:salmon">sempre</font> lo <font style="color:salmon">stesso nome della classe</font>.

- <font style="color:salmon">Inizializzano</font> i campi dell'oggetto.

- Anche se <font style="color:salmon">non hanno valori di uscita</font>, non si usa il [[Keywords|keyword Void]].

- <font style="color:salmon">Non è obbligatorio</font> specificare un costruttore per una classe.
  
  Se non viene specificato un <font style="color:springgreen">costruttore</font>, Java crea un <font style="color:salmon">costruttore di default</font>, questa sarà "vuota", cioè <font style="color:salmon">senza parametri</font>, che quindi crea oggetti con campi che hanno i loro valori di default.

- Si usa il [[Keywords|this]] all'interno dei costruttori per riferirsi al campo della classe perché gli argomenti hanno lo stesso nome dei campi.

# Objects
___

Per creare un oggetto servono $3$ passaggi:

- Dichiarazione
- Creazione
- Assegnazione
 ![center](https://i.imgur.com/IM9PMmE.png)

