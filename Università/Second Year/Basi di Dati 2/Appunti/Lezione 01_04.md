___

- Quando associazione 1..1 0..1, 1..1 1..1, chiedersi se è veramente necessario che sia una classe a parte e non un attributo di tale classe?

- Quando un oggetto ha molti stati va bene modellarlo usando molte classi is-a di quella classe
	- e.g. una partita ha degli stati: in corso, finito, sospeso
	- e.g. una prenotazione ha degli stati: accettato, cancellato, rifiutato

# Specifica della classe PartitaConRinuncia

- Se non lo si fa tramite associazioni

Operazioni di classe

rinunciatario(): Giocatore
	precondizioni: nessuna
	postcondizioni:
		- non modifica il livello estensionale
		- il risultato ('result') è così definito:
		- sia 'c' il valore dell'attributo this.rinuncia_colore.
		- se c=B
			- sia result: Giocatore tale che (result,this): bianco
		- se c=N
			- sia result: Giocatore tale che (result,this): nero


