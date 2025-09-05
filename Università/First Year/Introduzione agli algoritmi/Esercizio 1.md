
$T(n)=2T\left( \frac{n}{2} \right)+\theta(n)$
Caso base : $T(1)=\theta(1)$

## <font style="color:Indianred">Con metodo iterativo</font>

- prima iterazione con  $i=1$ abbiamo $T(n)=2T\left( \frac{n}{2} \right)+\theta(n)$
- seconda iterazione con $i=2$ abbiamo $T(n)=2\left( 2T\left( \frac{n}{2^2} \right)+\theta\left( \frac{n}{2} \right) \right)+\theta(n)$
	sviluppando diventa $T(n)=2^{2}\times T\left( \frac{n}{2^2} \right)+2\times\theta\left( \frac{n}{2} \right)+\theta(n)$
	semplificando diventa $T(n)=2^2+T\left( \frac{n}{2^2} \right)+\theta(n)+\theta(n)$
	quindi $T(n)=2^2+T\left( \frac{n}{2^2} \right)+2\times\theta(n)$

Notiamo allora un pattern dove a $i$ iterazioni avremmo $T(n)=2^i\times T\left( \frac{n}{2^i} \right)+i\times\theta(n)$

