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