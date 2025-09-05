___

- L'algoritmo <font style="color:salmon">Merge Sort</font> è un algoritmo ricorsivo che adotta una tecnica algoritmica detta Divide et Impera.

# Funzionamento

- $1)$ La sequenza di $n$ elementi viene divisa in due sottosequenze di $\frac{n}{2}$ elementi

- $2)$ Ripeti $1)$ finché le sottosequenze non hanno un solo elemento, quindi sono già ordinate per confronto ( o $<$ o $>$ )

- $3) Ricombina

![center](https://pic3.zhimg.com/v2-cdda3f11c6efbc01577f5c29a9066772_b.webp)

# Codice
```Python
def MergeSort(A, i, j): # T(n)
	if i < j:
		m = (i+j)//2 
		MergeSort(A, i, m) # T(n/2)
		MergeSort(A, m+1, j) # T(n/2)
		fondi(A, i, m, j) # S(n)

def fondi(A, i, m, j):
	a, b = i, m+1
	B = []
	while a <= m and b <= j:
		if A[a] <= A[b]:
			B.append(A[a])
			a+=1
		else:
			B.append(A[b])
	while a <= m: # la prima sottolista non è terminata
		B.append(A[a])
		a+=1
	while b <= j: # la seconda sottolista non è terminata
		B.append(A[b])
		b+=1
	for x in range(len(B)) # ricopio in A gli elementi in B
		A[i+x] = B[x]
```

# Costo

- La funzione MergeSort() senza fondi() costa $2T(\frac{n}{2})$

- La funzione fondi() costa $\theta(n)$

- La funzione MergeSort() completa costa $2T(\frac{n}{2})+\theta(n)$
  con $T(1) = \theta(1)$

- Quindi $T(n) = \theta(n\log n)$

# <font style="color:springgreen">Vantaggi</font>

- Tempo computazionale è $\theta(n\log n)$

# <font style="color:salmon">Svantaggi</font>

- L'operazione di fusione non si può fare in loco.
  Se si prova a farlo in loco il costo sale a $\theta(n^2)$

- I fattori costanti sono tali che l'[[Insertion Sort]] è più veloce del [[Merge Sort]] per valori piccoli di $n$.

- Quindi ha senso usare l'[[Insertion Sort]] dentro il [[Merge Sort]] quando i sottoproblemi diventano sufficientemente piccoli.

# Merge Insertion Sort ( Timsort )
```Python
def Merge_Insertion(A, i, j, k):
	dim = j – i + 1
	if dim > k:
		m = (i + j)// 2
		Merge_Insertion (A, i, m, k)
		Merge_Insertion (A,m + 1, j, k)
		Fondi(A, i, m, j)
	else Insertion_Sort(A, i, j)

Merge_Insertion(A, 0, len(A)-1, k) # chiamata iniziale
```

# Iterative Merge Sort
```Python
def Merge_Sort_Iter(A):
	n = len(A)
	l = 1
	while l < n:
		i = 0
		while i < n-l:
			fondi(A, i  i+l-1, min(n-1, i+ 2*l -1))
			i += 2*l
		l *= 2
```

- Il while interno viene eseguito $\theta(\frac{n}{l})$ volte e ciascuna volta costa $\theta(l)$ per un costo totale di $\theta(n)$.

- Il while più esterno viene eseguito $\log_2n$ volte ed ogni volta si paga un tempo $\theta(n)$.

- La complessità dell'algoritmo è pertanto $\theta(n\log n)$.

