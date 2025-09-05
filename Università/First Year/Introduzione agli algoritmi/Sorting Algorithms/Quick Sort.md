___

L'algoritmo <font style="color:salmon">Quick Sort</font> ha costo $O(n^2)$ nel caso peggiore ma nella pratica è spesso la soluzione migliore per grandi valori di $n$.


# Funzionamento

- $1)$ Nella sequenza di $n$ elementi si seleziona un <font style="color:salmon">pivot</font>. Questo viene posizionato nella sua giusta posizione in modo da ottenere due sottosequenze:
  - quella degli elementi minori o uguali al pivot.
  - e quella degli elementi maggiori al pivot.

- $2)$ Le due sottosequenze vengono ordinate ricorsivamente.

- $3)$ La ricorsione procede fino a quando le sottosequenze sono costituite da un solo elemento, quindi ordinato.

![center](https://camo.githubusercontent.com/1bb6a328593e513cff9c7375839f3c8b9967d5b85a98cec69e31757d4a878be2/68747470733a2f2f637572726963756c756d2d636f6e74656e742e73332e616d617a6f6e6177732e636f6d2f646174612d737472756374757265732d616e642d616c676f726974686d732f717569636b736f72742f717569636b5f736f72745f706172746974696f6e5f616e696d6174696f6e2e676966)

# Codice

```python
def Quick_Sort(A): # prima versione, non in loco.
	if len(A) <= 1:
		return A
	pivot = A[0]
	left, middle, right = [], [], []
	for x in A:
		if x<pivot:
			left.append(x)
		elif x==pivot:
			middle.append(x)
		else:
			right.append(x)
	return Quick_Sort(left) + middle + Quick_Sort(right)
```

```python
def Quick_Sort(A, i, j): # seconda versione, in loco.
	if i < j:
		p = Partition(A, i, j) # p è il pivot
		Quick_Sort(A, i, p-1)
		Quick_Sort(A, p+1, j)

def partition(A, a, b):
	pivot = A[a]
	i = a+1
	for j in range(a+1, b+1):
		if A[j] < pivot:
			A[j], A[i] = A[i], A[j]
			i += 1
	A[a], A[i-1] = A[i-1], A[a] # tutti gli elementi a destra del pivot 
								# sono maggiori o uguali a lui.
								
	return i-1 # restituisce l'index del pivot
```

- La funzione partiziona la porzione dell'array $A$ che va dalla posizione $a$ alla posizione $b$.
  
  Inizia <font style="color:salmon">scegliendo il primo elemento come pivot</font>.
  
  Successivamente, i due indici $i$ e $j$ vengono spostati verso destra a partire dalla destra del pivot.
  
  Ogni volta che l'indice $j$ è su un elemento inferiore al pivot <font style="color:salmon">avviene uno scambio degli elementi puntati dai due indici</font>.
  
  Dopo lo scambio <font style="color:salmon">si incrementa</font> $i$.
  
  Quando $j$ ha terminato di scorrere la porzione dell'array, <font style="color:salmon">il pivot viene spostato nella sua posizione corretta</font>: cioè la $i-1$.
  
  Si restituisce infine l'indice del pivot.
  ![center](https://i.imgur.com/TUofSf0.png)
# Costo

- $T(n) = T(k)+T(n-1-k)+\theta(n)$ se $n\geq2$ , dove $0\leq k<n$
- $T(0) = \theta(1)$

# <font style="color:springgreen">Vantaggi</font>

- Il suo tempo di esecuzione atteso è $\theta(n\log n)$.

- I fattori costanti nascosti sono molto piccoli.

- Permette l'ordinamento in loco.

- Caso <font style="color:springgreen">migliore</font> si verifica quando ad ogni passo, la dimensione dei due sottoproblemi è <font style="color:springgreen">identica</font>, in questo caso l'equazione di ricorrenza diventa:
  $T(n)=2T(\frac{n}{2})+\theta(n)$
  che si risolve in $T(n)=\theta(n\log n)$

# <font style="color:salmon">Svantaggi</font>

- Caso <font style="color:salmon">pessimo</font> si verifica quando il vettore è composto da elementi distinti <font style="color:salmon">già ordinati in modo crescente o decrescente</font>, in entrambi i casi infatti la ricorrenza diviene:
  $T(n)=T(n-1)+\theta(n)$ se $n\geq 2$
  che si risolve in $T(n)=\theta(n^2)$

