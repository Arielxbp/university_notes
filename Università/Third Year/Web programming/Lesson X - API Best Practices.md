___

Nelle URI inserire solamente __nomi__, e non i verbi, in quanto quelle sono calls HTTP

Usare lo `/` alla fine delle URI per le collezioni.
- Eg. `.../users/`

Usare i codici di stato specifici e inserire dettagli aggiuntivi nel payload della risposta, tramite l'aggiunta di dati nel corpo del codice di stato.

Per filtrare una ricerca usare le __query string__ all'interno delle URI invece di filtrare direttamente tramite il URI (path).
- E.g. `/managed-devices/?regione=USA` è OK.
- E.g. `/managed-devices/region/USA` non è OK.
Questo perchè la collezione è unica, quindi i parametri la limitano.

Non è consigliato l'inserimento di grandi dati binari all'interno di JSON per motivi di performance.
Per l'invio di tali dati è possibile procedere in due modi diversi:
- Inviare dati strutturati (JSON) e il file in un'unica richiesta (multipart)
- Caricare il file in una API dedicata e poi usare l'URL che viene restituito del file nella richiesta JSON principale.

Non è consigliato definire un corpo nelle richieste GET e DELETE.

Se una risorsa ha effetto solo su un utente, allora è meglio non annidarla direttamente sotto la risorsa che rappresenta l'entità target, ovvero l'utente.
Ma invece usare una collezione di risorse relative all'utente.
- E.g. `/users/{userid}/mute` non è OK.
- E.g. `/users/me/muted/{muted_user_id}` è meglio.

L'aggiornamento delle risorse viene effettuato tramite i due metodi PUT e PATCH
Il PUT sostituisce __completamente__ la risorsa target.

Il PATCH serve per effettuare modifiche __parziali__ a una risorsa. Non è __idempotente__ in quanto è possibile avere due PATCH concorrenti.
Serve per fare modifiche mirate, come cambiare solo un attributo di una risorsa.
- E.g. Mutare un utente, cambiare lo stato di una risorsa.

