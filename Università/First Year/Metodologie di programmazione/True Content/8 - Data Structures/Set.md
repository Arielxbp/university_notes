___

- Gli insiemi sono Collection che contengono elementi <font style="color:salmon">tutti distinti</font>.

- Le classi insiemi, <font style="color:salmon">HashSet</font>, <font style="color:salmon">TreeSet</font> e <font style="color:salmon">LinkedHashSet</font>, estendono <font style="color:salmon">AbstractSet</font> e implementano l'interfaccia <font style="color:springgreen">Set</font>.

>[!info] 
><font style="color:salmon">HashSet</font> memorizza gli elementi in una tabella di hash.
>
><font style="color:salmon">TreeSet</font> memorizza gli elementi in un albero mantenendo un ordine sugli elementi.
>
><font style="color:salmon">LinkedHashSet</font> memorizza gli elementi in ordine di inserimento.
# HashSet

- basato su <font style="color:salmon">Set</font>, una sottointerfaccia di [[Collections|Collection]] e di <font style="color:salmon">Iterable</font>.

- Come tutti gli altri <font style="color:springgreen">Set</font>, <font style="color:salmon">non contiene doppioni</font>.

- <font style="color:salmon">Non</font> è ordinato.

## How does it work

- Si fonda sul concetto di <font style="color:salmon">tabella hash</font>.

- Data in input un dato, lo si converte in una sequenza da cercare nell'Array base, in questo Array ogni index ha un puntatore indirizzato verso una <font style="color:salmon">lista linkata</font>. (credo, rivedere algoritmi per questo).

# TreeSet

- basato su <font style="color:salmon">Set</font>, una sottointerfaccia di [[Collections|Collection]] e di <font style="color:salmon">Iterable</font>.

- Come tutti gli altri <font style="color:springgreen">Set</font>, <font style="color:salmon">non contiene doppioni</font>.

- <font style="color:salmon">È</font> ordinato secondo l'ordinamento naturale del tipo <font style="color:salmon">String</font>, cioè in ordine alfabetico.

