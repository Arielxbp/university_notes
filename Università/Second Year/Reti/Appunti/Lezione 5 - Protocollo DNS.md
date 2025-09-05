___
# Identificazione degli host

- I nomi assegnati agli host Internet devono essere unici
- I nomi non danno indicazioni sulla collocazione degli host
- Quindi gli host vengono identificati tramite un indirizzi IP

# Indirizzo IP

- È costituito da 32 bit
- Ogni macchina possiede un indirizzo IP e un nome
- Il mapping tra nome e indirizzo IP di una macchina viene effettuato dal DNS
- Possiamo avere $2^{32}$ indirizzi IP (in quanto 32 bit)
# DNS (Domain Name System)

- Il DNS ha il compito di memorizzare e gestire tutti questi nomi degli host
- Possiede quindi un database implementato tramite una gerarchia di server DNS
- Viene utilizzato dagli altri protocolli al livello applicazione quando si necessita di tradurre hostname in indirizzi IP
- È implementato a livello applicazione, ovvero funziona all'interno delle macchine host e non nei router
- Ovvero è un applicazione che gira su ogni host

# Servizi DNS: Aliasing

- Un host può avere multipli alias, cioè altri hostname più semplici che si riferiscono al hostname canonico

# Servizi DNS: Distribuzione del carico

- I siti che vengono richiesti spesso, cioè con molto traffico, vengono replicati su multipli server
- Il sito replicato girerà su server diversi, quindi presentano tutti indirizzi IP differenti, perciò il hostname canonico del sito verrà associato a un insieme di indirizzi IP diversi
- Quando un client effettua una richiesta DNS per un sito tramite il suo hostname, il server risponderà scegliendo uno tra i vari indirizzi IP associati a quel hostname per distribuire il traffico sui server replicati

## Centralizzazione del DNS

- Il database non può essere memorizzato totalmente su un singolo server in quanto non sarebbe affidabile (se crasha il server DNS crasha tutto Internet)
- Inoltre il singolo server non potrebbe gestire la mole di richieste query proveniente da tutto il globo
- Quindi nessun server DNS mantiene il mapping di tutti gli host

## Gerarchia server DNS

- Si organizzano le 
- Vi sono 3 classi di server DNS, organizzati in una gerarchia
  - Root (radice), il client chiede al server Root indicazioni sul server DNS com, org, edu, ...
  - Top-level domain, il client chiede al server DNS com indicazioni per ottenere il server DNS di un sito.com
  - Authoritative

# Server DNS Root (Radice)

- In Internet ci sono 13 server DNS root
- Ognuno di questi 13 server sono replicati per motivi di affidabilità e sicurezza
- Si occupano di contattare i server DNS TLD se non ne conosce la mappatura, ottenerla e restituirla al richiedente, solitamente un server DNS locale

# Server TLD (Top-level domain)

- Questi server si occupano dei domini locali e non di alto livello come com, org, net, edu, it, fr, de

# Query Iterativa

- Una richiesta proveniente da un client viene mandato prima al server locale, questa chiederà a sua volta al server DNS root, che indirizzerà il server locale a chiedere al server DNS TLD, fino a raggiungere il server finale che restituirà l'indirizzo IP che si ha richiesto

# Query ricorsiva

- Una richiesta proveniente da un client viene mandato di volta in volta al server necessario finché non tornerà indietro con l'indirizzo IP richiesto

# DNS: Caching

- I server DNS si memorizzano nella loro cache locale la mappatura delle richieste effettuate, cioè si salvano il hostname con l'indirizzo IP restituito dalla prima richiesta per migliorare la loro efficienza
- Tipicamente i server DNS locali si memorizzano nella cache gli indirizzi IP dei server TLD
- Come conseguenza i server DNS root non vengono visitati spesso

# Record DNS

- I database memorizzano i record chiamati resource record (RR)
- Ogni messaggio di risposta DNS trasporta uno o più RR
- Un resource record è formato da nome, valore, tipo, tempo di vita rimanente
- MX ai server di autorità
- A e NS nei server DNS root (nei root solo RR per muoversi tra i server)

# Messaggi DNS

- Sia le richieste (query) che i messaggi di risposta usano lo stesso formato
- Ogni messaggio è formato dal: numero di identificazione, 

# UDP per Messaggi

- I messaggi usano il protocollo UDP in quanto non servono i vantaggi del TCP
- Se si perde il messaggio basta re-inviarlo
