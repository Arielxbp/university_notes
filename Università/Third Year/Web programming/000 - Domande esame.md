
1) Differenza tra virtual machine e docker, funzione scelta da lui.
2) Metodi http usate per le reazioni.
3) Mostrare il funzionamento di una funzione dal browser e poi mostrare il codice della funzione dalle api al backend, spiegando cosa facevo, facendo domande sui metodi http quando li nominavo, qualche codice di errore
4) Spiegare come viene gestito il login.
5) Sapere perché quel metodo http e non un altro.
6) Ha chiesto cosa significa REST.
7) che cosa vado a verificare nel db per fare far l’autenticazione del login e cosa succede se non trovo l’utente.
8) perché verifico un determinato dato e non un altro per vedere se sia presente un utente nel db.
9) poi mi ha chiesto di mostrargli dove effettuo una certa verifica in una determinata funzionalità che avevo implementato
10) Poi mi ha chiesto docker riga per riga i file che avevo scritto, sia i dockerfile che docker-compose.
11) Metodi http più varie cose/funzioni del tuo codice, potrebbe essere backend, frontend e/o dockerfile.
12) Fatto vedere il progetto, mi ha fatto creare una chat, inoltrare un messaggio e aggiungere reaction, poi gli ho fatto vedere come le ho implementate e le spunte.
13) A me ha chiesto simulare invio di messaggi , come ho implementato l'invio di messaggi e le spunte , come gestiscono gli errori in go , cosa si fa in caso di panic e il polling . Samory è stato molto tranquillo
14) Far vedere una funzione da Vue fino al database.
15) Differenza tra POST e PUT
16) Idempotenza
17) Chiede errori sulla correzione
18) Perché ci stanno due FROM nel dockerfile (nel multistage)
19) È PUT cacheable?
20) Gli stati delle funzioni asincrone/promise (in attesa risposta arrivata correttamente, risposta arrivata con errore/non arrivata).
21) Le risposte delle richieste cosa indicano (200, 400, ...).
22) La gestione del token di authentication (bearer auth)
23) A me ha fatto domande sul come funzionavano delle cose nel progetto ed ha voluto vedere il codice di alcune funzioni

___

defer(func()) viene eseguita alla fine del corpo in cui si trova il defer

http.responsewriter è usato per scrivere la risposta al client

r è usato per ottenere il corpo della richiesta
w è usato per scrivere la risposta
ps lo uso per ottenere i dati dalla URI (uniform resource identifier)

Gli attributi sono: `nome_attributo="valore"` che uso dentro ai tag html tipo \<class nome_attributo="valore">

il css non lo uso esplicitamente ma tramite l'attributo `style`

__DOM__ sta per document object model

`let` definisce una variabile con scope di blocco.

`var` definisce una variabili con scope di funzione.

`const` con scope di blocco.

assegnare a una variabile senza dichiararla la fa essere con scope globale

```js
setTimeout(() => {this.errormsg = null}, 3000)
// chiamo setTimeout passando come argomenti
// una funzione freccia () senza nome e senza argomenti
// che come corpo setta errormsg a null
// il secondo argomento che passo a setTimeout 3000
// indica tra quanto tempo setTimeout chiama la funzione
// freccia che gli ho passato
```


Il document object model è un modello di programmazione per documenti html e xml
Fornisce una rappresentazione strutturata del documento
E definisce un'interfaccia per interagire con l'albero e manipolare gli elementi

Tipo `document.getElementById("id")` trova un elemento per id

`export default` definisce l'esportazione principale, ogni modulo può avere una sola esportazione di default, e chiunque import il modulo lo usa se lo importa

utente interagisce -> framework reagisce -> __il framework aggiorna il dom__ -> utente vede i cambiamenti.

SFC sta per single file component ed è un file che contiene js html e css

SPA sta per single page application

Il file `main.js` è il punto di ingresso dell'applicazione, crea e monta l'app
In `app.vue` abbiamo il componente principale

Il router gestisce le rotte per le viste all'interno dell'app. Per navigare nell'applicazione

Usiamo vue con vite. Vite è un sistema di build per lo sviluppo web

vue ha delle direttive custom, tipo v-if e v-else

v-model bidirezionale cioè dom<-> js
v-bind è solo js->dom

mounted, beforeUnmount, ... sono __stati__ per le componenti.

All'interno di `mounted()` si esegue la logica che deve essere eseguita __dopo__ che il template è stato inserito nel DOM, quindi tipo logica che esegue il fetch iniziale di dati.

Una promise è un oggetto che si riferisci a un valore futuro.
Se una funzione restituisce una Promise, significa che il valore di ritorno sarà disponibile in futuro, cioè l'esecuzione è asicrona

Per usare una promise è necessario specificare:
- Una funzione che viene eseguita quando il risultato è disponibile.
- Una funzione che viene eseguita se qualcosa va storto.

Quindi una promise è in uno di questi stati:
- pending, prima di iniziare o il codice asincrono è in esecuzione
- fulfilled, l'operazione è stata completata con successo
- rejected, l'operazione è fallita.

Il pattern __async-await__ è un modo per scrivere codice asincrono.
Praticamente invece di usare Premise uso async function nome_function()

__Axios__ è un client HTTP per browser e node.js basato sulle Promise

La __Same origin policy__ è un meccanismo di sicurezza implementato nei browser, e serve per limitare la comunicazione tra script provieniente da origin diverse.

DUE URL HANNO LA STESSA __ORIGINE__ SE SONO IDENTIFIC IL PROTOCOLLO (http, https), DOMINIO (site.com) E LA PORTA(80, 8080,5173).

LA SOP __NON IMPEDISCE__ l'invio della richiesta, MA IMPEDISCE allo script malevolo di __leggere la risposta__ della richiesta HTTP
Tuttavia alcuni tag HTML possono comunque effettuare richieste Cross Origin

__CORS__ (Cross Origin Resource Sharing) è un meccanismo che permette ai server di specificare tramite header http quali origin possono accedere alle loro risorse.

___

Un container è un gruppo di processi linux

Docker e altri runtime di containers sono un'interfaccia utente user-friendly per tutte queste funzionalità del kernel linux di gestione container.

`docker run -p 8080:80`
avvia il container sulla sua porta 80 virtuale
aggiunge una regola di firewall all'host che reindirizza il traffico in arrivo sulla porta 8080 dell'host alla porta 80 del container.

IL CONTAINER CONDIVIDE CON L'HOST IL KERNEL DEL OS DELL'HOST

Le risorse hardware sono condivise tra host e containers.

```dockerfile
# Immagine base
FROM python:3.11-slim

# Directory di lavoro
WORKDIR /app

# Dipendenze
COPY requirements.txt .
RUN pip install -r requirements.txt

# Codice sorgente
COPY . .

# Comando di avvio
CMD ["python", "app.py"]
```

Per buildare l'immagine: `docker build -t app .`

Per eseguire l'immagine: `docker run -p 8080:8080 app`

```bash
sudo docker build -p Dockerfile.backend -t wasatext-backend .

sudo docker build -p Dockerfile.frontend -t wasatext-frontend .

sudo docker run --rm --name wasatext-backend -p 3000:3000 wasatext-backend

sudo docker run --rm --name wasatext-frontend -p 5173:80 wasatext-frontend

```