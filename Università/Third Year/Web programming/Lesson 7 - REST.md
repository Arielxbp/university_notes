___


REST è uno __stile__ architetturale per progettare in modo indipendente servizi e applicazioni web.


Le URI servono per identificare in modo univoco le risorse.

Un sistema per essere RESTful deve avere dei vincoli necessari:
- Deve essere client-server
- Non deve avere stato (stateless)
- Deve essere cacheable
	- Questa cache serve al sistema per mantenere lo stato.
- Deve avere un interfaccia uniforme (uniform-interface)
- Deve avere un sistema a strati (layered system)

## Client-Server

## Stateless

Ogni richiesta inoltrata dal client deve contenere tutte le informazzini necessarie per essere compresa.

Il client __non__ può sfruttrare nessun contesto memorizzato sul server.

Lo stato della sessione è mantenuto interamente sul client, mentre lo stato della risorsa è mantenuto sul server.

### Interfaccia uniforme

Ogni componente deve necessariamente usare un'interfaccia uniforme, ovvero con una stessa struttura base, come protocollo usato, struttura del messaggio.

Ciò semplifica la progettazione del sistema al costo della sua efficienza.

