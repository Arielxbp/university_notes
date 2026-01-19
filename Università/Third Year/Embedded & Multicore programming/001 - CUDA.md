___

GPUs are designed with __throughput__ in mind:
- More cores but less cache and control.

Le GPU sono progettate per avere un alta capacità di rendimento.

Una GPU possiede:
- Frequenza di clock moderata.
- Piccole cache.
- Controlli semplici, senza predizioni di branch.
- Unità di calcolo efficienti dal punto di vista energetico.
- Interfacce con alta larghezza di banda per la memoria e lo scambio di dati con l'host.

Le unità di calcolo sono efficienti, ma presentano una latenza molto alta:
- Richiedono molti thread per tollerare questa latenza.

# Architettura di una GPU con capacità CUDA

## Streaming multiprocessor (SM)

Streaming multiprocessor sono le unità meno granulari all'interno di una GPU.

Queste contengono streaming processor (SP), che sono i CUDA cores.

Le SPs che stanno all'interno di una stessa SM:
- Condividono la logica di controllo e la cache delle istruzioni da eseguire.

Due o più SM formano un "building block"

Ogni thread ha una posizione in un blocco 1D, 2D o 3D.

Ogni blocco ha una posizione in una griglia 1D, 2D o 3D.

Ogni thread è a conoscenza della sua posizione all'interno della struttura generale, grazie a un insieme di variabili intrinsece.

Un thread grazie a questa conoscenza può mappare la sua posizione al sottoinsieme di dati alla quale viene assegnato.

La dimensione dei blocchi e delle griglie sono determinate dalla __capacità__, che determina cosa riesce a fare ogni generazione di GPU.

La capacità computazionale di un dispositivo è rappresentato da un numero che indica la versione. (Chiamato SM version)

Questo valore numerico identifica le caratteristiche supportate dal hardware della GPU ed è usato dalle applicazioni a tempo di esecuzione per determinare quali caratteristiche hardware e istruzioni sono disponibili sulla GPU presente.

# Come scrivere un programma CUDA

Serve specificare una funzione che verrà eseguita da tutti i thread.

Questa funzione è chiamato __kernel__.

Il programmatore deve specificare quanti threads sono organizzati nella griglia e nei blocchi.

```C
dim3 b(3, 3, 3);
dim3 g(20, 100);

foo<<<g, b>>>(); // Esegue una griglia 20x100 fatta di blocchi 3x3x3 threads

foo<<<10, b>>>(); // Esegue una griglia di 10 blocchi dove ogni blocco è 3x3x3 threads

foo<<<g, 256>>>(); // Esegue una griglia 20x100 fatta di 256 threads

```
