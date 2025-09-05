___

- L'algortimo <font style="color:salmon">Bucket Sort</font> è un algoritmo che può avere tempo computazionale minimo $O(n)$.

# Funzionamento

- $1)$ Si creano $k$ <font style="color:salmon">buckets</font> in base a una costante opportuna attraverso la formula $k=\frac{elementi}{costante}$
  Questi $k$ buckets vengono inseriti dentro una lista $X$. (una lista di liste)

- $2)$ Iterando sulla lista $A$ data in input, l'elemento $x$ viene inserito nell' i-esimo bucket attraverso la formula $X[\lfloor k \cdot \frac{x}{M+1}\rfloor]$ dove $M$ è il numero più grande.

- $3)$ Dopo aver scorso tutta la lista $A$, si ordinano gli elementi di ciascun bucket.

- $4)$ Infine si concatenano tutti i bucket ordinati.

![center](https://i.imgur.com/nqVjN18.png)


>[!attention] 
>Il costo computazionale dipenderà dall'algoritmo utilizzato per ordinare i vari buckets.
>Questo conta sul fatto che gli elementi in input sono uniformemente distribuiti, in quanto non ci si aspetta che molti elementi finiscano nello stesso bucket.
>
>TLDR: ci si aspetta che ogni bucket abbia circa gli stessi numeri.
# <font style="color:springgreen">Vantaggi</font>

- Possibile tempo computazionale $O(n)$

- Caso ottimo si ha $T(n)=\theta(n)+n \times \theta(costo \space per \space ordinare \space \theta(1) \space elementi)$.
  
  quindi $T(n)=\theta(n)+\theta(n)\cdot \theta(1)=\theta(n)$.

# <font style="color:salmon">Svantaggi</font>

- Non in loco, costo spaziale presente.

- Tempo computazionale non fisso.

- Caso pessimo si ha $T(n)=\theta(n)+\theta(costo \space per \space ordinare \space n \space elementi)$.

