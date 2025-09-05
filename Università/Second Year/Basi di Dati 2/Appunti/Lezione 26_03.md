___

- È possibile che non ci siano precondizioni
- Nelle post-condizioni è necessario indicare se l'operazione eseguita modifica o meno il livello estensionale, inoltre serve definire il valore del risultato
- Se una cosa è possibile rappresentarlo in UML, allora va rappresentato in UML, anche se è possibile rappresentarlo come tipi di dato o come operazioni
- Possiamo assegnare degli attributi come opzionali (il diagramma diventa però molto implicito -> no bueno)
- Se un dato può variare in valore nel tempo, è meglio implementarlo come operazione della classe
- Pensare se un dato è accettabile da inserire manualmente per ogni record
- Quasi mai usare tipo enumerativo, sempre fare con le generalizzazioni o associazioni con classi
- Se un requisito presenta sotto-requisiti, è meglio implementare il requisito non come attributo ma meglio come classe apparte con i sotto-requisiti come attributi di quella classe (e.g. requisiti che dipendono dal tipo di un oggetto)