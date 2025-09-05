## Esercizio 1

>[!domanda]
>Un client (browser) vuole accedere alla pagina web di un sito: "http://www.example.com/index.html". Il sito è ospitato su un server web che utilizza il protocollo HTTP/1.1
>
>1) Quale richiesta HTTP invierà il browser per ottenere la pagina? Scrivere l’header completo della richiesta HTTP che il client invia al server.
>2) Se la richiesta è corretta e il file index.html esiste, quale codice di stato HTTP restituirà il server? Scrivere l’header della risposta HTTP che il server potrebbe inviare.
>3) Se la pagina index.html non esiste, quale codice di stato restituirà il server?
>4) Se l’accesso alla pagina è vietato per motivi di autorizzazione, quale codice di stato verrà restituito?

- GET /index.html HTTP/1.1
- 