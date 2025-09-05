___

# Logica

- Ogni logica è definita da una __sintassi__ e una __semantica__
- La sintassi considera il linguaggio come l'insieme delle sequenze finite di simboli ammesse dal linguaggio, dove ogni simbolo fa parte di un alfabeto
- La sintassi definisce la struttura delle formule
- La semantica definisce il significato di ogni formula della logica

# Alfabeto della logica del primo ordine

- È composto da:
	- Insieme $V$ di variabili
	- Insieme $F$ di simboli di funzione, ognuno dei quali ha associato il suo numero di argomenti detto __arità__
	- Insieme $P$ di simboli di predicato, ognuno dei quali ha associato il suo numero di argomenti detto __arità__
	- Connettivi logici
	- Quantificatori
	- Simboli speciali quali la parentesi aperta, quella chiusa, e la virgola
- Per rifersi a un simbolo di funzione $f$ o a un simbolo di predicato $p$ di arità $k$, si scrive rispettivamente $f/k$ e $p/k$
- I simboli di funzione di arità $0$ vengono anche detti simboli di costante

- esempi:
	- $succ/1$ significa $succ(X)$, che è il numero naturale $X+1$, ovvero il successore di $X$

# Termine

- Ogni variabile è un termine
- Ogni simbolo di costante è un termine
- Se $f$ è un simbolo di funzione applicata a termini, allora $f$ è un termine

- Un termine rappresenta un oggetto di interesse

# Formula

- Se $p$ è un simbolo di predicato di arità $n$ e $t_{1},\dots,t_{n}$ sono termini, allora $p(t_{1},\dots,t_{n})$ è una formula
