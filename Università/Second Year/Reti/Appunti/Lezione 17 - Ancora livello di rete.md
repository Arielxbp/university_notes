___

## Link state

Lo stato di un link indica il costo associato a tale link, quindi se il costo è infinito significa che il collegamento (link) __non esiste__ o che è stato interrotto.

Ogni nodo deve conoscere i costi di tutti i collegamenti della rete, e per fare ciò esiste un database che mantiene la mappa completa della rete.
Questo database è __unico__ per tutta la rete e ogni nodo della rete ne possiede una copia.
Il database viene rappresentato come una matrice.

Ogni nodo per conoscere i propri vicini e i costi dei collegamenti verso loro:
- Invia messaggi di hello su tutte le sue interfacce.

Ogni nodo che riceve tali messaggi:
- Crea la lista dei vicini con i relativi costi, chiamata LSP, cioè LS packet.

Ogni nodo esegue un flooding dei LSP, cioè invia a tutti i vicini il proprio LSP e quando ne riceve uno __nuovo__, allora lo ri-inoltra a tutti i suoi vicini tranne quello da cui lo ha ricevuto.

Per costruire l'albero a costo minimo utilizzando il LS database, ogni nodo deve eseguire l'algoritmo di Dijkstra.

## Protocollo OSPF

È un protocollo a stato del collegamento (link state).

Utilizza il __flooding__ di informazioni di stato del collegamento e l'algoritmo di Dijkstra per determinare i percorsi a costo minimo.

Il flooding nel protocollo è tale per cui:
- Si invia periodicamente messaggi OSPF all'intero sistema autonomo, utilizzando il flooding.
- Ogni volta che si verifica un cambiamento nello stato di un collegamento, il router manda informazioni di instradamento a tutti gli altri router.

