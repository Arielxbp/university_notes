___

# Termine

Ogni variabile è un termine.

Ogni simbolo di costante è un termine.

Se $f$ è un simbolo di funzione di arità $n>0$ e $t_{1},\dots,t_{n}$ sono termini, allora $f(t_{1},\dots,t_{n})$ è un termine.

# Formula

>[!attention]
>
__QUANTIFICATORE $+$ VARIABILE $+$ FORMULA__

Se $p$ è un simbolo di predicato di arità $n$ e $t_{1},\dots,t_{n}$ sono __termini__, allora $p(t_{1},\dots,t_{n})$ è una formula.

Se $\phi$ e $\psi$ sono formule, allora lo sono anche:
- ($\phi$)
- $\neg\phi$
- $\phi \wedge\psi$
- $\phi \vee \psi$
- $\phi \rightarrow\psi$
- $\phi\leftrightarrow\psi$

Se $\phi$ è una formula e $X$ è una variabile, allora sono formule anche:
- $\forall X\phi$
- $\exists X\phi$


Per essere una formula ci deve essere almeno un predicato:
- $foo(X)$

# Predicato

asd

# Interpretazione

Una interpretazione è una funzione $I$ che assegna un __valore di verità__ ad ogni lettera proposizionale.

Un __modello__ è una interpretazione che rende vera una formula.

Una formula può essere:
- __Soddisfacibile__, cioè esiste una interpretazione che è un suo modello.
- __Valida__, cioè ogni interpretazione è un suo modello.
- __Insoddisfacibile__, cioè nessuna interpretazione è un suo modello.
## Esempio

Formula: $\rho:a\wedge(b\vee c)$
Lettere proposizionali in $\rho:\{a,b,c\}$
Interpretazione: $I:I(a)=true, I(b)=true, I(c)=false$
allora la formula proposizionale $\rho$ è __vera__ nell'interpretazione $I$.
Cioè l'interpretazione $I$ è un modello di $\rho:I\models\rho$

## Esempio

La formula:$$(a\wedge b)\wedge(\neg a\wedge\neg b)$$
sarà sempre falsa qualsiasi siano le interpretazioni per $a$ e $b$.

# Pre-interpretazione

Sia $F$ un insieme di simboli di funzione.
Una pre-interpretazione $prel$ per $F$ è costituita da:
- un insieme non vuoto $D:$ il dominio di interpretazione.
- Una corrispondenza che associa a ogni simbolo di funzione ${f/n}\in F$ di arità $n \geq 0$ una funzione del tipo $D^{n}\rightarrow D$ denotata $prel(f)$.


# Funzione eval

Dati $V,F$ e $P$, e sia $\phi$ l'insieme di tutte le formule che possono essere generate da $V,F$ e $P$.
Sia $I$ una interpretazione su $P$ che include una pre-interpretazione $prel$ su $F$. Sia inoltre $S$ un assegnamento alle variabili $V$ per $prel$.
Definiamo, in dipendenza da $I$ e da $S$, la funzione$$eval^{I,S}:\phi\rightarrow {\{true,false\}}$$
