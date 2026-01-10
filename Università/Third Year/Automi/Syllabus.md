___


DFA=NFA

Definire CNF, CFG=CFG in CNF, 2n-1 passi per stringa lunga n

Linguaggio regolare sse regex descrive tale linguaggio

Pumping lemma

CFG=PDA

///

Esistono linguaggi non decidibili e anche non riconoscibili ($A_{TM}$ usando diagonalizzazione)

L è decidibile sse L è riconoscibile e coRiconoscibile

Linguaggio riconoscibile sse esiste TM multinastro che lo riconosce (TM multinastro equivalente TM classica)

Per ogni NTM ne esiste una deterministica equivalente (Creo multinastro simula computazione ramo albero)

Definire concetto riducibilità tramite funzione, mostrare se A riducibile a B e B decidibile allora A decidibile, e A indecidibile allora B indecidibile

Primo di godel

Secondo di godel

///

Definire le classi PSPACE e NPSPACE, dimostrare che PSPACE=NPSPACE (Savitch)

Definire la complessità di spazio, enunciare e dimostrare il teorema di Savitch (Grafo -> configurazioni -> esistenza di ramo di configurazioni -> path -> path è SPACE(logn^2))

Definire le classi P, NP e la nozione di NP-completezza, mostrare che se P=NP allora NP coincide con NP-completo (Due Linguaggi riduzione da uno all'altro)

Enunciare e dimostrare il teorema di gerarchia di tempo (Diagonalizzo usando t1 << t1.5 << t2)

Enunciare e dimostrare il teorema di gerarchia di spazio, utilizzare il teorema per mostrare che PSPACE contenuto non uguale a EXPSPACE 

Definire la classe coNP e il problema UNSAT, dimostrare che UNSAT è coNP-completo

Definire il concetto di riduzione polinomiale, dimostrare che 3COL riducibile polinomialmente a SAT (definisci verificatore che verifica ogni arco no nodi stesso RGB -> verificatore computa in tempo poly -> 3COL è NP)

///

DTIME(n^5) = NTIME(n^5) (Computazione suddivisibile in n^3 blocchi consecutivi da n^2 passi ciascuno -> linguaggio dove (C,C') computazioni raggiungibile in minore uguale n^2 passi) -> linguaggio per ipotesi decidibile in tempo n^2 -> definisco verificatore che usa R per verificare sequenza di computazioni -> verificatore costa n^5 quindi NTIME contenuto in DTIME)

Tecnica della diagonalizzazione (Esiste D decisore di ATM (o linguaggio che si vuole dimostrare indecidibile) -> Definisco H che su input TM M esegue D su M,M -> se accetta rifiuta e rifiuta accetta -> eseguo H su H -> contraddizione)

3COL riducibile polinomialmente a 4COL (Due grafi uno in 3COL e uno in 4COL -> definisco funzione che dato il primo grafo mi da il secondo -> Se G in 3COL aggiungo nodo e lo coloro con quarto colore -> ok -> se G in 4COL il nuovo nodo deve avere colore diverso da tutti gli altri -> quindi G' in 3COL)






## Automi

- [x] DFA
- [x] Configurazione
- [x] Linguaggi regolari
- [ ] Operazioni sui linguaggi
	- [ ] Unione
	- [ ] Intersezione
	- [ ] Complemento
	- [ ] Concatenazione
	- [ ] Potenza
- [ ] Teoremi di chiusura dei linguaggi regolari
- [x] Non determinismo
- [x] Classe dei linguaggi riconosciuti da un DFA: L(DFA) = REG
- [x] Classe dei linguaggi riconosciuti da un NFA: L(NFA)
- [x] Teorema REG = L(DFA) = L(NFA). Dimostrazione è mostrare la costruzione di un DFA a partire da un NFA
- [x]  Espressioni regolari
- [x] Teorema REG = RE. Dimostrazione è costruire per tutti i casi base un nfa corrispondente e usare chiusura operazioni e ipotesi induttiva per i casi unione concatenazione e star per regex. L'altra parte usare gnfa
- [x] GNFA 
- [x] Trasformazione da GNFA a espressione regolare. Dimostrazione è togliere stati e aggiungere sulle etichette la regex parziale
- [x] Pumping lemma
- [x] Grammatiche acontestuali CFG
- [x] Derivazione e produzione
- [ ] Tecniche per construire grammatiche
- [ ] Conversione da DFA a CFG __da rivedere__
- [x] Forma normale di Chomsky CNF
- [x] Teorema: ogni CFG ammette una CFG equivalente in forma normale
- [x] PDA
- [x] Lemma: conversione da CFG a PDA + conversione da PDA a CFG (molto lungo)
- [x] Pumping lemma per CFG (Non lo chiede spero)

- [ ] TM
- [ ] 