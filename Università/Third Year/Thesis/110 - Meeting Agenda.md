___

This is an agenda of every meeting done during the Internship with the thesis supervisor.

## Meeting 1

Objective:
- Introduction and initial work discussion.

Topics:
- Research done about SoTA approaches to matrix diagonalization in DFT.
- Found ELPA2 as an eigenproblem solver using SoTA methods.
- Discussion about the math background used by various SoTA eigenproblem solvers.

Questions for the meeting:
- Next steps.

Notes obtained during the meeting:
- Tenstorrent architecture introduction.

Assigned next steps:
- [ ] Try to write simple kernels involving matrices. ($50\%$)
- [x] Begin to write the thesis introduction section: Scrivere il capitolo della relazione sul "background", in cui descrive gli approcci esistenti (quelli principali allo stato dell'arte) per la diagonalizzazione. ($100\%$)

## Meeting 2

Objective:
- 

Topics:
- Mostrare mat_add in tt-lang 
- Mostrare la sezione "background" della tesi su overleaf
- Chiedere quanto testo scrivere per un topic specifico, e quanto dettagliato si deve spiegare un argomento che si deve introdurre. (leggi domanda 2.1)

Questions for the meeting:
- Spiego cosa è DFT all'interno del paper o lo menziono soltanto siccome è inerente 
- Serve spiegare le nozioni di algebra lineare sulle matrici? (Tipo cosa è una matrice ortogonale, tridiagonale, a banda, ...)
	- Tipo come la ricomposizione di RQ porti A in una forma diagonale dopo varie iterazioni?
- Riguardo alla tesi, è consigliato utilizzare il template della Sapienza sin da subito oppure intanto scrivo solamente il contenuto. E solo alla fine lo rifinisco all'interno del template?
- Come procedere dal punto di vista del codice (tt-lang), in quanto la documentazione mi sembra insufficiente, e online non si riescono a trovare
  risorse (repo, esempi, programmi) che utilizzino tt-lang in modo esaustivo. Per esempio non si può fare debugging sui kernel e molte volte restituiscono errori strani.
- Chiedere se conosce altre risorse su tt-lang o su come funzionano altri domain specific language con architettura a tiles/blocchi (triton, cutile) 
- Versioni di pip, problemi con sudo, compilazione in locale della versione di python.
- Non riesco ad immaginarmi come funzionano le operazioni delle matrici in tiles e non in elementi. E la documentazione non è molto dettagliata a riguardo.
- Possibilità di usare tt-nn o tt-metallium intanto invece di tt-lang.


Notes obtained during the meeting:
- Come target devo considerare un professore di informatica, conoscenza base ma non dettagliata.
- Si evita argomenti base.
- Basta menzionare DFT. Basta anche una sola frase.
- 

Assigned next steps:
- [ ] Far funzionare un qualsiasi algoritmo per diagonalizzare usando tt-metallium, tt-nn o tt-lang.
- [x] Spiegare brevemente cosa è la QR decomposition.
- [x] Spiegare brevemente cosa è Householder reflections.
- [x] Spiegare brevemente cosa è Cuppen's D&C.
- [x] Quindi espandere le descrizioni dei vari algoritmi in modo che si capisca bene cosa fanno.

## Meeting 3

Objective:
- 

Topics:
- 

Questions for the meeting:
- 

Notes obtained during the meeting:
- 

Assigned next steps:
- [ ] 
