___

Una catena di Markov a tempo discreto è una tupla $(U, X, Y, p, g)$, dove:
- $U$ è l'insieme dei valori di input della catena (può essere vuoto), ovvero rappresenta i possibili input che il sistema può ricevere.
- $X$ è l'insieme non vuoto che definisce tutti i possibili stati in cui il sistema può trovarsi.
- $Y$ è l'insieme non vuoto che rappresenta i possibili output del sistema.
- $p$ è la funzione di probabilità di transizione, che calcola la probabilità che la catena si sposti da uno stato a un'altro quando riceve un input.
	- La somma delle probabilità di tutte le possibili transizioni da uno stato $x$ deve essere __sempre uguale__ a $1$.
	- $$\prod_ip_{i}=1$$
- $g$ è la funzione di output, che determina l'output generato dal sistema quando si trova in un determinato stato.

