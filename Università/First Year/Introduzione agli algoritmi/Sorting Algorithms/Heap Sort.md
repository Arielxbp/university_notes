___

- L'algoritmo <font style="color:salmon">Heap Sort</font> è un algoritmo di ordinamento complesso ma che esibisce ottime caratteristiche.

- È una <font style="color:salmon">Struttura dati</font>.

- In Python questa è implementata nella libreria standard <font style="color:salmon">heapq</font>.
# Funzioni possedute

- <font style="color:salmon">Per creare la struttura</font>: heapify(A), trasforma una lista $A$ arbitraria di $n$ elementi in un heap minimo. <font style="color:salmon">Tempo richiesto</font>: $O(n)$

- <font style="color:salmon">Per estrarre il minimo</font>: heappop(A), rimuove e restituisce l'elemento minimo della lista e ristabilisce la proprietà di heap minimo. <font style="color:salmon">Tempo richiesto</font>: $O(\log |A|)$

- <font style="color:salmon">Per inserire un elemento</font>: heappush(A, x), inserisce l'elemento  $x$ in modo che l'heap mantenga  la proprietà di essere heap minimo. <font style="color:salmon">Tempo richiesto</font>: $O(\log|A|)$

# Caratteristiche

- Quando viene usato la funzione di ordinamento su una lista $A$, gli elementi all'interno della lista $A$ vengono risistemati in modo da rispettare una forma debole di ordinamento: <font style="color:salmon">ordinamento verticale</font>.
  
  Anche se questo ordinamento non è perfetto, il primo elemento sarà comunque il minimo tra tutti gli elementi della lista $A$.

- La radice dell'albero binario corrisponde ad $A[0]$.

- il figlio sinistro del nodo che corrisponde all'elemento $A[i]$, se esiste, corrisponde all'elemento $A[2i+1]$.

- il figlio destro del nodo che corrisponde all'elemento $A[i]$, se esiste, corrisponde all'elemento $A[2i+2]$.

- il padre del nodo che corrisponde all'elemento $A[i]$ corrisponde all'elemento $A[\lfloor \frac{i - 1}{2} \rfloor]$. (intero minore più vicino al quoziente)

- Poiché lo heap ha tutti i livelli completamente pieni tranne al più l'ultimo, la sua <font style="color:salmon">altezza</font> è $O(\log n)$.

![center](https://i.imgur.com/unCM2Uz.png)

# Funzionamento

- $1)$ Partendo dalle ultime due foglie, compara due elementi della stessa riga e prendi la più grande tra le due, chiamala $x$. 

- $2)$ Compara $x$ con il padre dei due elementi comparati in $1)$, se $x$ è maggiore del padre, allora scambiali di posto.

- $3)$ Se si ha effettuato lo scambio tra $x$ e il padre $y$, compara i figli di $y$, prendere il maggiore e compararlo con $y$, se $y$ è ancora minore, scambia di nuovo la posizione dei due elementi. Ripetere questo passaggio finché non si arriva alle foglie o finché $y$ non sia maggiore di suo figlio.

- 3) Ripeti $1)$ e $2)$ con gli elementi precedenti alle ultime due della stessa riga.

- $4)$ Una volta arrivati alla radice dell'albero, scambiare di posizione la radice con l'ultima foglia, e dopo averlo fatto, togliere l'ultima foglia dallo heap.

- $5)$ Compara i figli della radice, scegliere il maggiore tra i due e compararlo con la radice, se il figlio è maggiore allora scambiali di posizione, dopo aver effettuato lo scambio, similmente al passaggio $3)$, comparare finché non si arriva alle foglie o non si trova un elemento minore.

- $6)$ Dopo aver finito di comparare del passaggio $5)$, similmente a $4)$, scambiare di nuovo la radice con l'ultima foglia, e dopo lo scambio togliere l'ultima foglia dallo heap.

- Alla fine di questi passaggi si avrà la lista in input ordinata <font style="color:salmon">non debolmente</font>, cioè si avrà una lista veramente ordinata.

# <font style="color:springgreen">Vantaggi</font>

- Ordinamento in loco

- come [[Merge Sort]] ha un costo computazionale di $O(n\log n)$ anche nel caso peggiore.

