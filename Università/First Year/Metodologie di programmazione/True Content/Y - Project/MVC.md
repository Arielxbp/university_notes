___

Modello
Vista
Controllo
permette l'invio di messaggi con chi è in osservazione
observer 

# Modello
___

- il modello non deve avere nessuna dipendenza
- indipendente all 100%
- non deve avere bottoni
# Vista
___

- aggiorna le entità
- deve rappresentare solo questo gioco, quindi dipende del tutto dagli altri 2
- 

# Controllo
___

- observer observable
- dipende dal modello per il 50%
- definire actionPerformed() 


il main 
view osservatrice del modello
gameloop richiama l'aggiornamento del modello
main deve fare thread.slip 

_________

