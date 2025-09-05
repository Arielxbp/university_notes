___

# Funzionamento

- $1)$ Si trova il numero $k$, cioè l'elemento più grande dell'array $A$ da ordinare.

- $2)$ Si inizializza un nuovo array $C$ con dimensione pari a $k$.
  
  Quindi se in $A$ il numero massimo è $42$, allora l'array $C$ avrà $42$ posizioni.
  
- $3)$ Si scorre $A$ e per ogni indice $i$ si incrementa il contatore $C[A[i]]$ delle occorrenze di $A[i]$.
  
  Quindi se $A[2]=5$, allora nel counter presente in $C[5]$ andrò ad aumentarlo di $1$ questo counter.

- $4)$ Dopo aver scorso $A$, si va ad scorrere $C$ e per ogni indice $i$ si inserisce $C[i]$ occorrenze dell'elemento $i$ in $A$.
  
  Quindi se $C[1]=4$, allora si inseriranno $4$ volte $1$ all'interno dell'array $A$.

![center](https://i.imgur.com/y3u6kdR.png)

# Codice
```python
def Counting_Sort(A):
	k=max(A)
	n=len(A)
	
	C=[0]*(k+1) # creo l'array C 

	for i in range(n): # calcolo le occorrenze degli elementi in A
		C[A[i]]+=1

	j=0
	for i in range(len(C)) # reinserisco in A gli elementi in ordine
		for _ in range(C[i])
			A[j] = i
			j+=1
```

# <font style="color:springgreen">Vantaggi</font>

- Tempo computazionale è $\theta(n+k)$ dove $k$ è il numero più grande della lista.

# <font style="color:salmon">Svantaggi</font>

- Costo proporzionale al numero più grande numericamente presente all'interno della lista $A$.
