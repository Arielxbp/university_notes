Un grafo è un insieme di $n$ nodi collegati da $m$ archi

## Grafi diretti

- Un grafo si chiama diretto quando i suoi archi hanno un verso/direzione
- In un grafo diretto si ha il numero massimo di archi quando ogni nodo possiede $n-1$ archi che lo collegano agli altri $n-1$ nodi, cioè $m=n(n-1)$
## Grafi indiretti/non diretti

- Un grafo si chiama indiretto/non diretto quando i suoi archi non hanno un verso/direzione
- In un grafo indiretto si ha il numero massimo di archi quando ogni nodo possiede $n-1$ archi che lo collegano agli altri $n-1$ nodi, ma dato che gli archi non hanno una direzione, si dovrà dividere per 2 il risultato, cioè $m=\frac{n(n-1)}{2}$

# Grafi sparsi

- Un grafo si dice __sparso__ se $m=O(n)$
- Cioè se il numero degli archi è nell'ordine di $n$

## Albero

- L'albero è un grafo __connesso__ senza __cicli__
- L'albero è un esempio di grafo sparso perché avrà sempre $n$ nodi con $n-1$ archi

# Grafi densi

- Un grafo si dice __denso__ se $m=\Omega(n^2)$

## Grafo completo

- Un grafo si dice __completo__ se ha tutti gli archi, e quindi è denso

Possono esistere grafi non sparsi ma neanche densi:
- Un grafo può avere $\theta(n\log n)$ archi

# Rappresentazione di un grafo

- Un grafo può essere rappresentato in due modi:
	1) Matrice di adiacenza
	2) Liste di adiacenza

## Matrici di adiacenza

- Dato un grafo e la sua rappresentazione tramite matrice di adiacenza $M$, la cella $M[i][j]=1$ se e solo se c'è un arco diretto da $i$ a $j$

## Liste di adiacenza

- Dato un grafo e la sua rappresentazione tramite liste di adiacenza $G$, questa lista contiene tanti elementi quanti sono i nodi del grafo.
- $G[x]$ è una lista contenente i nodi adiacenti al nodo $x$, ovvero quei nodi raggiunti da archi che partono da $x$
- Usando questa rappresentazione si ottiene un notevole risparmio di spazio nel caso di grafi sparsi

# Grado di un nodo

- Il grado di un nodo è il __numero di archi__ che includono il nodo
- Se il grafo è __diretto__ allora si suddivide il grado nel grado __entrante__ e il grado __uscente__, cioè rispettivamente il numero di archi che puntano al nodo, e il numero di archi che partono dal nodo considerato

# Pozzi

- Un pozzo è un nodo __senza archi uscenti__
- Esistono solamente nei __grafi diretti__
- In un grafo diretto possono essere presenti $n$ pozzi, ed è quando ogni nodo non presenta archi (?)

## Pozzi universali

- Un pozzo universale è un pozzo che viene raggiunto da __tutti gli altri nodi__ del grafo
- Se esiste il pozzo universale in un grafo, questo è __unico__

# Depth First Search (Algoritmo)
```python
def DFS(u, G):
	//
	def DFSr(u, G):
		visitati[u]=1 # segno il nodo u come visitato
		for v in G[u]: # per ogni nodo adiacente v di u
			if visitati[v]==0: # se non l'ho ancora visitato
				DFSr(v, G) # lo visito
	//
	visitati=[0]*len(G) # creo la lista dei visitati
	DFSr(u, G)
	return visitati
```

- I nodi attraversati tramite gli archi effettivamente utilizzati dall'algoritmo e quest'ultimi formano quello che è un __albero DFS__
## Complessità

- La complessità dell'algoritmo è $O(n+m)$
- Attraverso l'__analisi ammortizzata__ l'iterazione su tutte le liste di adiacenza ci costa al massimo $O(m)$

# Albero DFS

- Un albero DFS viene a formarsi dopo una visita DFS
- Un albero DFS può essere memorizzato tramite il __vettore dei padri__
- È assicurato la formazione di un albero DFS perché ogni nodo già visitato non potrà __mai__ essere rivisitato, impedendo così la __creazione di cicli__ (si ricorda che non si deve avere cicli per essere un albero)
- Se il grafo è __diretto__ allora l'albero potrebbe avere un numero __diverso__ di nodi in base al nodo radice
- Se il grafo è __indiretto__ allora l'albero ha __sempre__ un numero __uguale__ di nodi indipendentemente da quale nodo radice si parte

# Vettore dei padri (Algoritmo)
```python
def Padri(u, G):
	//
	def DFSr(u, G, P):
		for v in G[u]: # per ogni nodo adiacente v di u
			if P[v]==-1: # se non ha ancora un padre assegnato
				P[v]=u # allora viene assegnato al nodo u
				DFSr(v, G, P)
	//
	P=[-1]*len(G)
	P[u]=u # il padre del nodo radice è se stesso
	DFSr(u, G, P)
	return P
```

- Il vettore dei padri $P$ di un albero di un grafo di $n$ nodi ha $n$ elementi
- Se $u$ è un nodo dell'albero DFS:
	- $P[u]$ contiene il padre del nodo $u$
- Il nodo radice per convenzione ha come padre se stesso
- Se $u$ non è un nodo dell'albero allora $P[u]$ contiene $-1$
- __!__ Il vettore dei padri dell'albero DFS permette di ricavare facilmente un cammino fra due nodi $u$ e $v$

## Complessità

- La complessità dell'algoritmo è $O(n+m)$
- Attraverso l'__analisi ammortizzata__ l'iterazione su tutte le liste di adiacenza ci costa al massimo $O(m)$

# Cammino dalla radice a un nodo (Algoritmo)
```python
def Cammino(u, P):
	if P[u]==-1:
		return []
	cammino=[]
	while u!=P[u]:
		cammino.append(u)
		u=P[u]
	cammino.append(u)
	cammino.reverse()
	return cammino
```

## Complessità

- La complessità dell'algoritmo è $O(n)$
- Questo perché nel caso peggiore il while itera su tutti i $n$ nodi, cosa che accade quando l'albero è una catena e il nodo $u$ e l'unico figlio dell'albero

# Colorazione di grafi

- Un grafo è colorato quando per ogni nodo del grafo, i suoi adiacenti sono colorati in modo diverso

## Grafi 2-colorabile
```python
def Colora(G):
	//
	def DFSr(u, G, Colore, c):
		Colore[u]=c
		for v in G[u]:
			if Colore[v]==-1:
				DFSr(v, G, Colore, 1-c)
	//
	Colore=[-1]*len(G)
	DFSr(0, G, Colore, 0)
	return Colore
```
- Un grafo è $2$-colorabile se e solo se __non contiene cicli__ di lunghezza __dispari__
- Un ciclo di lunghezza dispari rende impossibile la colorazione del grafo con due colori
### Prova di correttezza

- Siano $x$ e $y$ due nodi adiacenti in $G$, consideriamo i due possibili casi e dimostriamo che in entrambi i casi i due nodi al termine dell'algoritmo avranno colori opposti:
	1) L'arco $(x,y)$ viene attraversato durante la visita
		- In questo caso banalmente i due nodi hanno colori distinti
	2) L'arco $(x,y)$ __non__ viene attraversato durante la visita
		- Esiste un cammino in $G$ che da $x$ porta a $y$, questo cammino si chiude a formare un ciclo con l'arco $(y,x)$. Il ciclo è di lunghezza pari __per ipotesi__, quindi il cammino è di lunghezza dispari, e poiché sul cammino i nodi si alternano i colori, alla fine $x$ avrà colore diverso da $y$

### Complessità

- La complessità dell'algoritmo di bi-colorazione è $O(n+m)=O(m)$ perché in un grafo connesso $m\geq n-1$ (?)

# Componenti connesse (Algoritmo)
```python
def Componenti(G):
	//
	def DFSr(u, G, C, c):
		C[u]=c # il nodo u appartiene alla componente c
		for v in G[u]: # ora per ogni nodo v collegato a u
			if C[v]==0: # se non è ancora stato inserito in una componente
				DFSr(v, G, C, c) # allora la inserisco nella stessa componente di u
	//
	C=[0]*len(G) # init della lista delle componenti
	c=0 # init del counter delle componenti
	for nodo in range(len(G)): # per ogni nodo del grafo G
		if C[nodo]==0: # se il nodo attualmente considerato non è stato ancora assegnato a una componente
			c+=1 # inizializzo una nuova componente
			DFSr(nodo, G, C, c) # e assegno a questa nuova componente il nodo libero
	return C
```

- Quando si parla di componenti connesse si parla di __grafi indiretti__
- Una componente connessa di un grafo è un sottografo composto da un insieme di nodi connessi fra di loro
- Un grafo si dice __connesso__ se ha __una sola__ componente connessa, ovvero quando tutti i nodi sono collegati fra di loro

## Complessità

- La complessità dell'algoritmo per ottenere la lista delle componenti connesse in un grafo indiretto è $O(n+m)$

# Grafo trasposto di un grafo
```python
def Trasposto(G):
	GT=[[] for _ in G] # init delle liste di adiacenza del grafo trasposto
	for u in range(len(G)): # per ogni nodo u
		for v in G[u]: # itero sui suoi nodi adiacenti v
			GT[v].append(u) # e assegno a ogni nodo adiacente v il nodo u
	return GT
```
- Dato un grafo __diretto__ $G$, il grafo trasposto di $G$, denotato con $G^T$, è un grafo che ha gli stessi nodi di $G$ ma con gli archi che hanno __direzione opposta__
- I nodi che in $G$ che riescono ad arrivare a un nodo $u$ sono i nodi che in $G^T$ vengono raggiunti a partire da $u$

# Componenti fortemente connesse (Algoritmo)
```python
# Algoritmo per calcolare la componente fortemente connessa alla quale appartiene un nodo u
def ComponentiFC(u,G):
	visitati1=DFS(u, G) # mi calcolo i nodi raggiungibili dal nodo u
	GT=Trasposto(G) # mi calcolo il grafo trasposto di G
	visitati2=DFS(u, GT) # uso il grafo trasposto per calcolare i nodi che riescono a raggiungere il nodo u
	componente=[] # init della lista dei nodi appartenente alla stessa componente fortemente connessa del nodo u
	for i in range(len(G)): # per ogni nodo del grafo
		if visitati1[i]==visitati2[i]: # se raggiunge e viene raggiunto dal nodo u
			componente.append(i) # allora tale nodo viene inserito nella lista
	return componente
```

- Quando si parla di componenti fortemente connesse si parla di __grafi diretti__
- Una componente fortemente connessa di un grafo è un sottografo composto da un insieme di nodi tali che __ogni__ nodo dell'insieme riesce a raggiungere tramite archi diretti __tutti gli altri nodi__ dell'insieme
- Un grafo si dice __fortemente connesso__ se ha __una sola__ componente (fortemente connessa)

## Complessità

- La complessità dell'algoritmo per calcolare la componente fortemente connessa alla quale appartiene un nodo u del grafo è $O(n+m)$:
	- La lista visitati1 costa $O(n+m)$ in quanto si esegue una visita DFS che parte da $u$ in $G$
	- L'algoritmo per calcolare il grafo trasposto $GT$ costa $O(n+m)$
	- La lista visitati2 costa $O(n+m)$ in quanto si esegue una visita DFS che parte da $u$ in $G$
	- Il for itera su tutti i nodi del grafo, quindi costa $O(n)$

## Algoritmo per calcolare tutte le componenti fortemente connesse di un grafo
```python
def compFC(G):
	FC=[0]*len(G) # init del vettore delle componenti fortemente connesse del grafo
	c=0 # init del counter delle componenti fortemente connesse
	for i in range(len(G)): # per ogni nodo in G
		if FC[i]==0: # se non è ancora stato assegnato a una componente
			E=ComponentiFC(i, G) # allora mi trovo tutta la componente fortemente connessa alla quale appartiene
			c+=1
			for u in E: # e per ogni nodo appartenente alla componente appena trovata
				FC[u]=c # assegno lo stesso identificatore per raggrupparli nel vettore delle componenti fortemente connesse
	return FC
```

- __!__ Esistono diversi algoritmi che lavorano in tempo $O(n+m)$ per calcolare il vettore delle componenti fortemente connesse (e.g. algoritmo di Tarjan, algoritmo di Kosaraju)
### Complessità

- La complessità dell'algoritmo è $\theta(n)\cdot O(n+m)=O(n^2+nm)=O(n^2+n\cdot n^2)=O(n^3)$
- Nel caso peggiore si può avere un grafo $G$ che presenta $\theta(n^2)$ archi e $n$ componenti fortemente connesse





