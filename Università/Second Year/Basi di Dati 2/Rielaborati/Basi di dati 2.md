- Questo rielaborato salta i concetti base sui __diagrammi UML__ delle classi e degli oggetti.

# Vincolo di identificazione di classe (UML)

Un vincolo di identificazione di classe:
- Impone che non possono esistere allo stesso tempo oggetti di una classe che hanno gli stessi valori per un insieme di attributi.
- impone che non possono esistere allo stesso tempo oggetti di una classe che sono collegati tramite link agli stessi oggetti di altre classi.

> [!Note] Ricorda
> Un vincolo di identificazione di classe può coinvolgere solo attributi a molteplicità [1..1] e/o ruoli della classe a molteplicità 1..1

Per esempio se si vuole modellare la frase:
- Non possono esistere due studenti con la stessa matricola nella stessa università.
- ![|500](https://i.imgur.com/ZYm2gsT.png)

# Specializzazione di operazioni di classe

Dato un operazione di una classe $x$, se questa presenta una sottoclasse $y$ che deve prima specializzare l'operazione definita in $x$ per poterla utilizzare, allora la specializzazione __non__ andrà a modificare la __segnatura__ dell'operazione, ovvero:
- Deve avere lo stesso numero e tipo di argomenti.
- Il tipo di ritorno dell'operazione nella sottoclasse è dello stesso tipo o un sottotipo di quello dell'operazione nella superclasse.

Cosa è stato specializzato dell'operazione viene specificato nella __specifica della classe__.

# Diagramma UML degli use-case

I diagrammi degli use-case modellano le __funzionalità__ che il sistema deve realizzare.

Uno __use-case__ cattura un insieme omogeneo di funzionalità che vengono accedute da un gruppo omogeneo di utenti.

Un __attore__ è un ruolo che un utente gioca interagendo con il sistema.
Inoltre uno stesso utente può essere rappresentato da più attori e più utenti possono essere rappresentati dallo stesso attore.

Un attore $B$ può fare le veci di un attore $A$, e facendolo ne eredita tutte le associazioni. 

Un associazione nel diagramma degli use-case modella la possibilità di accesso da parte di un attore alle funzionalità di uno use-case.

Tra use-case possono presentarsi dipendenze:
- Inclusione.
- Estensione.
- Generalizzazione.

## Dipendenze tra use-case: Inclusione

Dati due use-case $A$ e $B$, si ha un inclusione tra queste quando:
- Alcune funzionalità dello use-case $A$ hanno bisogno di usare alcune funzionalità dello use-case $B$.

E.g. si ha necessità di suddividere lo use-case per la gestione degli esami, in due use-case, uno per somministrare gli esami, e uno per la creazione e valutazione degli esami.
Questi due use-case andranno a __includere__ lo use-case per la gestione degli esami.

![|500](https://i.imgur.com/sBhhrBy.png)

## Dipendenze tra use-case: Estensione

Dati due use-case $A$ e $B$, si ha una estensione tra queste quando:
- In alcuni casi particolari, alcune funzionalità dello use-case $A$ sono __estese__ con le funzionalità dello use-case $B$.

E.g. quando gli studenti si iscrivono ai corsi, durante il processo di iscrizione, possono optare per il pagamento online.

![|500](https://i.imgur.com/THNmc3z.png)


> [!Note] Ricorda
> L'estensione presenta il verso del collegamento puntato verso lo use-case che ha bisogno delle funzionalità altrui.

## Dipendenze tra use-case: Generalizzazione

Dati due use-case $A$ e $B$, si ha una generalizzazione tra queste quando:
- In alcuni casi particolari, alcune funzionalità dello use-case $A$ sono rimpiazzate con le funzionalità dello use-case $B$.

E.g. quando gli studenti si identificano sul sito, l'identificazione online avviene tramite password o tramite l'impronta digitale.

![|500](https://i.imgur.com/vK66b9W.png)

# Documenti di specifica

Il diagramma UML delle classi e quello degli use-case hanno bisogno di documenti di specifica che definiscono alcuni elementi presenti al loro interno.

Questi documenti sono di $4$ tipi:
- Specifica dei tipi di dato.
- Specifica di classe.
- Specifica di uno use-case.
- Specifica dei vincoli esterni.

## Documento di specifica dei vincoli esterni

Spesso i requisiti provenienti da regole del dominio applicativo, ovvero le __business rules__, non possono essere modellate nel diagramma delle classi, quindi vanno specificati nel documento di specifica dei vincoli esterni.

Ogni vincolo esterno si definisce nel documento con questi due elementi:
- Un identificatore univoco.
	- E.g. \[V.classi_a_cui_il_vincolo_si_applica.nome_vincolo]
- Una asserzione che definisce quali sono le condizioni che devono essere soddisfatte dagli oggetti o dai link in modo che siano in una configurazione legale per il vincolo.

Nel caso in cui un vincolo si applica agli oggetti di una sola classe, è raccomandato definire tale vincolo nella specifica di quella classe piuttosto che nella specifica dei vincoli esterni.

# FOL

Per scrivere "Ogni persona ha solo un codice fiscale":
$$\forall p\space Persona(p) \rightarrow \lnot(\exists v_{1},v_{2}\space v_{1}\neq v_{2} \land CF(p,v_{1}) \land CF(p,v_{2}))$$
pag 67 A.4 per altri esempi

# Regole di precedenza (FOL)

In FOL vengono usate le regole di precedenza per la valutazione dei connettivi e quantificatori.

Quindi:
- La negazione $\neg$ viene prima di tutti gli altri.
- I connettivi $\land$ e $\lor$ vengono dopo il $\neg$.
- I quantificatori $\forall$ e $\exists$ vengono dopo i quantificatori.
- Le inclusioni $\rightarrow$ e $\leftrightarrow$ vengono dopo tutti.

# Analisi usando FOL

Attraverso l'uso del First Order Logic (FOL) è possibile definire ciò che non è definibile mediante diagrammi, ovvero:
- Vincoli sui dati, esterni al diagramma delle classi.
- Specifiche delle operazioni di classe e di use-case.

## Simboli di predicato per le classi

Ogni classe $C$ presente nel diagramma delle classi definisce il simbolo di predicato unario $C/1$.

Quindi dato:
- Un qualsiasi elemento $x$. 
se $$C(x)=true$$ allora $x$ è un'istanza della classe $C$.

## Simboli di predicato per domini (tipi degli attributi)

Ogni dominio $dom$ utilizzato nello schema concettuale definisce il simbolo di predicato unario $dom/1$.

Quindi dato un qualsiasi elemento $x$, se $dom(x)$ restituisce $true$ allora $x$ è un valore di tipo $dom$.

Quindi dato:
- Un numero $x$.
se $$Intero(x)=true$$ allora $x$ è un numero intero.

## Simboli di predicato per attributi

Ogni attributo $attr$ di una classe del diagramma delle classi definisce il simbolo di predicato binario $attr/2$.

Quindi data:
- Un'istanza $x\in C$.
- Un attributo $attr$.
- Un valore $val$ del tipo dell'attributo $attr$.
se $$attr(x, val)=true$$
allora $val$ è un attributo con valore $val$ di $x$.

> [!NOTE] ricorda
> Se si usassero i simboli di funzione per formalizzare attributi, non si potrebbero supportare attributi con più valori.
> E.g. una persona $x$ può avere più di una email, ma se si usasse $email(x)$ non sarebbe possibile restituire tutte le email della persona $x$.

## Simboli di predicato per associazioni

Ogni associazione $assoc$ tra due classi $C_{1}$ e $C_{2}$ presente nel diagramma delle classi definisce il simbolo di predicato binario $assoc/2$.

Quindi data:
- Un'istanza $a\in A$.
- Un'istanza $b\in B$.
- Un'associazione $assoc$ tra le due classi.
se $$assoc(a,b)=true$$ allora esiste un link tra le due istanze.

## Simboli di predicato per attributi di associazione

Ogni attributo $attr$ di una associazione $assoc$ binaria del diagramma definisce il simbolo di predicato ternario $attr/3$.

Quindi data:
- Un'istanza $a\in A$.
- Un'istanza $b\in B$.
- Un'associazione $assoc$ tra le due classi contenente un attributo $attr$.
se $$attr(a,b,val)=true$$
allora esiste un link tra le due istanze che ha come valore dell'attributo $attr$ esattamente $val$.

## ASd

Data un associazione tra due classi:$$\forall c_{1},c_{2} \space assoc(c_{1},c_{2})\rightarrow C_{1}(c_{1})\land C_{2}(c_{2})$$
Dato un attributo (nome) di una classe (Città):$$\forall x,v\space nome(x,v)\land Città(x)\rightarrow Stringa(v)$$

## Vincoli di cardinalità sui ruoli di associazioni

Dato un associazione con vincolo di cardinalità 1..*
deve essere vero che:$$\forall d\space Dipartimento(d)\rightarrow \exists p_{1}\space lavora(d,p_{1})$$
se per esempio in un qualsiasi dipartimento ci deve essere almeno una persona che ci lavora.

