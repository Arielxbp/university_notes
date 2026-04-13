___

Legge di amdhal e in quali condizioni disattivare la l1 porta vantaggi su cuda

Risposta(?):La l1 ha blocchi da 128B e la l2 da 64B, se non usi i dati overfetched con la l1 attiva carichi il doppio della roba senza motivo saturando di più la banda

___

Tipologie di MPI_Send  
Scope delle variabili OMP

___
  
- Come funzionano e come si gestiscono i nested for loops con OpenMP  
- Quando ha senso disattivare la L1 in CUDA

___

- I vari livelli di comunicazione tra thread e MPI (funneled, serialized...)  
- i derived datatypes in MPI

___

- Cosa sono i bank. Quando abbiamo bank conflict e il broadcast dei bank.  
- MPI_Status : i field. Quali sono le situazioni in cui non sappiamo tag o chi ci ha mandato i dati e dobbiamo prenderli con Status. Errori MPI. Come prendiamo il numero di dati che abbiamo ricevuto in una comunicazione e perche potremmo ricevere meno dati di buf_size.  
- parallelizzare questo ciclo for  
```c
for (int i = 2; i < N; i++) {
	A[i] = A[i - 2] + A[i] * 0.5;
}
```

___

- Data una percentuale di codice sequenziale quanto è lo speedup massimo  
- Quando ha senso spegnere la L1 in CUDA

___

a me invece ha chiesto i bank conflicts e perché non c’è false sharing in CUDA

___

-false sharing  
-tramite esercizio SoA e AoS  
-Cosa occupa più spazio AoS o SoA

___

D: Legge di Amdahl: R: Ogni programma è caratterizzato da una frazione seriale che non può essere parallelizzata e quindi pone un limite allo speedup che possiamo ottenere. La legge di Amdahl serve a fare una stima asintotica che converge a 1/(1 - a), dove 0 <= a <= 1 è la frazione parallelizzabile del programma.

D: Tra Array of Structs e Struct of Arrays, qual è la più adatta su GPU? R: Struct of Arrays perché permette di sfruttare gli accessi coalescenti su un campo della struttura. 

D: Come si gestisce il loop scheduling su OpenMP? R: Si specifica la clausola schedule(kind, chunksize), dove: - kind è la tipologia di scheduling: static (chunk assegnati prima dell'esecuzione), dynamic (chunk assegnati durante l'esecuzione, i thread che terminano il proprio chunk ne possono richiedere un altro), guided (come dynamic ma la dimensione dei chunk futuri assegnati diminuisce durante lo svolgimento del loop), auto (sceglie il compilatore o il sistema di runtime) o runtime (sceglie il programmatore, tipicamente tramite environmental variable). - chunksize è il numero di iterazioni assegnato ai thread: se non è specificato, l'argomento di default è 1. N.B.: Aspettatevi domande sulle tipologie di scheduling. Esempio: se specifico chunksize su guided scheduling, questa è la dimensione del chunk all'inizio o alla fine?. 

D: Quando si verificano i bank conflicts su CUDA? R: La shared memory è organizzata in banchi intrecciati in modo tale che thread che vogliono accedere a indirizzi diversi su banchi diversi possono farlo in parallelo. Se però thread diversi voglioni accedere a indirizzi che stanno sullo stesso banco, si verifica un conflitto e gli accessi vengono serializzati. Eccezione: se tutti i thread di un warp provano ad accedere allo stesso indirizzo, la shared memory coordina una "broadcast read" e trasmette il valore nell'indirizzo a tutti i thread, senza causare serializzazioni. 

D: Come si svolge cudaMemcpy() tra GPU e CPU? R: A livello hardware, i trasferimenti tra GPU e CPU coinvolgono direct memory access e memoria virtuale. 

D: Perché non c'è false sharing su GPU? R: Ogni streaming multiprocessor ha una sua cache L1, la quale è condivisa solo tra i thread in quel multiprocessor. 

D: Quando si verifica il false sharing? R: Il false sharing si verifica quando thread diversi modificano variabili, anche diverse, nella stessa linea di cache e finiscono per invalidarsi a vicenda, scambiando linee di cache ma non dati. Alcune soluzioni comuni includono la mappatura thread-variabili, il padding (che però spreca memoria) o l'uso di variabili locali/private. 

D: Vantaggi degli Struct of Arrays? R: Permettono gli accessi coalescenti dato che elementi dello stesso campo sono salvati nella stessa array in indirizzi vicini che verrebbero letti nello stesso burst e occupano meno memoria in confronto alle Array of Structs. 

D: A cosa serve MPI_Status? R: MPI_Status è una struttura create da operazioni MPI_Recv() o MPI_Wait() per riassumere l'esito dell'operazione. Per MPI_Recv(), campi principali di questa struttura sono MPI_SOURCE, che indica il processo mittente, MPI_TAG, che indica il tag del messaggio, e MPI_ERROR, che è un codice di errore che indica se l'operazione ha avuto successo (0 o MPI_SUCCESS) o meno (codice non zero, ad esempio MPI_ERR_TRUNCATE). 

D: Si consideri un loop annidato dove il loop esterno fa 10 iterazioni e il loop interno fa 1000000 di iterazioni e un altro loop annidato dove il loop esterno fa 1000000 di iterazioni e il loop interno fa 10 iterazioni: usando 16 thread, com'è conveniente parallelizzare questi loop? R: In linea di massima è preferibile parallelizzare il loop con più iterazioni. Tuttavia, nel primo caso, può essere conveniente parallelizzare il loop esterno e introdurre collapse(2) per distribuire meglio il carico di lavoro.