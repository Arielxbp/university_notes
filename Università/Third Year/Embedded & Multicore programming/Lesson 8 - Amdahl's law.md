___

All'interno di un'applicazione esistono $2$ parti di istruzioni:
- Una parte che può essere parallelizzata.
- Una parte necessariamente seriale (e.g. lettura da disco), chiamata __frazione seriale__.

La frazione seriale è un valore $1-\alpha$, quindi $\leq 1$, dove $\alpha$ indica la parte parallelizzabile dell'applicazione.

La legge di Amdahl enuncia che l'aumento di velocità data dalla parallelizzazione è limitata dalla frazione seriale.

La formula per calcolare il tempo ottimizzato è:$$T_{parallel}(p)=(1-\alpha)T_{serial}+\alpha \frac{T_{serial}}{p}$$
Quindi se $\alpha=0$, allora il codice non può essere parallelizzabile.

# Gustafson's law

Formulata dopo la legge di Amdahl, che non tiene in considerazione il __weak scaling__, considerata invece dalla legge di Gustafson.

Considerando il weak scaling, la frazione parallela aumenta all'aumentare della dimensione del problema.

Quindi mentre il tempo seriale rimane costante, quello parallelo aumenta.

La frazione seriale può aumentare all'aumentare del numero di processori, causato principalmente dall'__overhead__ dovuto allo scambio di contesto tra vari processi nel processore. (causato anche dalle collettive)

