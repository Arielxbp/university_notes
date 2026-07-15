
## Transpose of a matrix

La trasposta di una matrice è una matrice dove gli elementi fuori dalla diagonale sono flippati rispetto alla diagonale.

## Symmetric matrices

Una matrice simmetrica è una matrice quadrata tale che è uguale alla sua __trasposta__.
$$A=A^T$$
Una delle proprietà utili è che matrici simmetriche con soli elementi reali presentano sempre autovalori reali. Inoltre gli autovettori sono __ortogonali__ tra loro.

### Orthogonal eigenvectors

Autovettori che sono ortogonali tra loro significa che sono perfettamente __perpendicolari__.

Dati due autovettori, questi sono ortogonali se il loro prodotto è uguale a zero.
Per matrici simmetriche reali si usa il __prodotto a punti__ (per vettori ovviamente).
Per matrici hermitiane complesse si usa il __prodotto interno__, ovvero si prende il complesso coniugato trasposto del primo vettore prima di moltiplicarlo a punti per il secondo.

In meccanica quantistica, gli autovettori rappresentano stati quantici. Se due autovettori sono ortogonali, significa che che questi due stati fisici sono __completamente indipendenti e mutualmente esclusive tra di loro__.

### Orthonormal eigenvectors

Autovettori che sono sia ortogonali e anche __normalizzati__ (la lunghezza è $1$), vengono chiamati __ortonormali__.
$$Q^{-1}=Q^\dagger$$

Una matrice ortonormale $Q$ ha la proprietà che la sua inversa è semplicemente la sua trasposta. Ciò comporta che il passo di trasformazione inversa nell'algoritmo di diagonalizzazione sia molto veloce da computare e comporta pochi costi.

## Hermitian matrices ($A{^{\dagger}}$)

Una matrice hermitiana di una matrice $A$ è ottenuta tramite la trasposizione di tale matrice, e durante la trasposizione __si invertono i segni degli elementi contenenti valori immaginari__.

Poiché un elemento sulla diagonale principale necessariamente deve essere __uguale__ al proprio complesso coniugato, la diagonale principale di una matrice hermitiana può contenere solamente numeri strettamente reali.

È la proprietà più importante delle matrici all'interno del contesto DFT, in quanto matrici hamiltoniane devono garantire la computazione di autovalori __strettamente reali__.

Tutte le matrici hermitiane sono matematicamente garantite di produrre autovalori strettamente reali.

Se una matrice è composta strettamente da valori reali, allora l'essere hermitiana è esattamente la stessa cosa di essere simmetrica.

## Hamiltonian matrices

In contesto DFT, per matrice hamiltoniana si intende una matrice che rappresenta l'operatore hamiltoniano $\hat{H}$. (usato per catturare l'energia cinetica e potenziale degli elettroni)

In un contesto prettamente matematico, una matrice hamiltoniana è un tipo specifico di matrice $M$ dove i suoi elementi sono blocchi $2n\times2n$.

## General

Ogni algoritmo usato per eseguire una diagonalizzazione di matrici si basa sulla computazione del __problema generalizzato dei autovalori__ $$Hx = \lambda x$$
dove $\lambda$ sono gli autovalori, che nel contesto DFT corrispondono alle energie orbitali degli elettroni, la $x$ indica gli autovettori, che rappresentano i coefficienti delle funzioni d'ond per quei elettroni.

Un __eigenpair__ è semplicemente la coppia di un autovalore con il suo autovettore corrispondente.

## Direct Eigensolvers

Un __eigensolver diretto__ è un algoritmo che computa gli eigenpairs in tempo $O(N^3)$, dove $N$ indica la dimensione della matrice.

### Iterative Solvers

Rispetto agli eigensolvers diretti, quelli __iterativi__, Davidson e/o Lanczos, __ipotizzano__ una soluzione e __affinano__ tale soluzione tramite cicli per trovare solo alcuni autovalori estremi.

Nel contesto della teoria funzionale della densità (DFT), gli algoritmo diretti vengono preferiti, ma si stanno cercano ottimizzazioni in quanto il loro costo proibitivo per dimensioni grandi.

## Characteristics of the hamiltonian matrix in DFT context

Le matrici hamiltoniane sono matrici __dense__, cioè quasi tutti i suoi elementi sono diversi da zero.

Trovare gli eigenpairs di matrici dense è inefficiente, quindi gli algoritmi __trasformano__ le matrici dense in matrici sparse (più semplici), prima di risolverle.

## Banded matrix

Una matrice a banda indica una matrice dove tutti i suoi elementi diversi da zero sono limitati in una "banda" diagonale che consiste in quella principale, più un numero di diagonali sopra la principale e un numero di diagonali sotto la principale.

Tutti gli elementi fuori da tale banda sono nulli (zero).

### Tridiagonal matrix

Una matrice tridiagonale è un caso specifico di matrice a banda, dove il numero di diagonali sopra la principale e il numero di diagonali sotto la principale è $1$.

Una volta che una matrice è nella sua forma tridiagonale, per trovare i suoi eigenpairs costa computazionalmente $O(N^2)$, dove $N$ è la dimensione della matrice.

## Risolutori a due fasi (Two-Stage Solver)

Per risolvere il bottleneck causato dalla limitata quantità di memoria, librerie allo stato dell'arte impiegano due fasi per risolvere il problema.

La prima fase comporta la riduzione della matrice densa in input in una matrice a banda, usando moltiplicazione di tipo __BLAS3__. (non utilizzano memoria credo?)

La seconda fase comporta la riduzione ulteriore da matrice a banda in una matrice tridiagonale. (La computazione è limitata dalla memoria, ma il bottleneck è diminuito in quanto la matrice presenta solo elementi non nulli all'interno della banda)

## Trasformazione inversa

Dato che la matrice originaria $H$ è stata ridotta in una matrice più semplice $T$ per trovare gli eigenpairs più facilmente. Gli autovettori computati appartengono a $T$ e non a $H$.

Definendo $Q$ come la matrice contenente tutte le trasformazioni matematiche applicate per ottenere $T$ partendo da $H$, bisogna applicare $Q$ agli autovettori ottenuti per mapparli nello spazio fisico originale.

Quindi:
- Se $y$ è un autovettore della matrice tridiagonale, l'autovettore DFT $x$ sarà uguale a $Qy$, $$x=Qy$$
In un risolutore a due fasi, anche la trasformazione inversa viene fatta in due passi. Si trasformano i vettori dalla base tridiagonale alla base a banda, e poi dalla base a banda alla base densa.

## Results

Dopo la riduzione a due fasi, la matrice risultante è tridiagonale, e applicando un algoritmo iterativo come divide et impera o MRRR, si vanno ad azzerare i rimanenti elementi non nulli fuori dalle diagonali.

La matrice finale è completamente diagonale, dunque gli elementi su tale diagonale sono gli autovalori.

Le trasformazioni matematiche effettuate sulla matrice costituiscono una nuova matrice, questa è la matrice degli autovettori corrispondenti.

# Pytorch (Torch)

## torch.tensor

A `torch.Tensor` is a multi-dimensional __matrix__ containing elements of a single data type.

These can be constructed from a `list` or using the constructor `torch.tensor()`:
```python
torch.tensor([1, 1], [1, 1])
```

Keep in mind that `torch.tensor()` __always__ copies data.
If creating using a numpy array, we can avoid copying data by using `torch.as_tensor()` instead.

## bfloat16 and float32, Automatic Mixed Precision (AMP)

When using `torch.bfloat16`, we are trading precision for an improvement in range, this is particularly useful when underflow and overflow are possible.

While both consume the same amount of bytes, bfloat16 mimics the range of float32 but is less precise.

When training models, to prevent values from dropping to absolute zero, underflow, or spiking to infinity, overflow, typically automatic mixed precision (AMP) must be implemented with an active loss scaler such as `torch.cuda.amp.GradScaler`.

## torch.device

A `torch.device` is an object representing the device on which a `torch.tensor` is or will be allocated.

Most commonly this would be "cpu" or "cuda".

