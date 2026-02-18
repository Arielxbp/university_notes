___

## Mini Sample Test

Si consideri un software sviluppato seguendo un approccio plan-driven implementato con tre fasi: F1, F2, F3 ciascuna con costo A. Le "change request" possono arrivare solo al fine di una fase e provocano la ripetizione (con relativo costo) di tutte le fasi che precedono. Si assuma che dopo la fase F3 (cioè al termine dello sviluppo) arriva una change request. Qual'e' il costo totale per lo sviluppo del software in questione.

1) 4\*A
2) 5\*A
3) 6\*A <

___

Si consideri un software sviluppato seguendo un approccio iterativo implementato con due fasi: F1 seguita da F2. Ciascuna fase ha costo A e deve essere ripetuta una seconda volta con probabilità p. Qual'e' il costo atteso dello sviluppo dell'intero software?

1) 3\*A\*(p + 1)
2) 2\*A\*(p + 2)
3) 2\*A\*(p +1) <

___

Quale delle seguenti frasi meglio descrive l'obiettivo del "check di completezza" che è parte della "requirements validation activity".

1) Assicurarsi che per ogni requisito sia stato implementato nel sistema.
2) Assicurarsi che i requisiti funzionali descrivano tutte le funzionalità del sistema.
3) Assicurarsi che i requisisti descrivano tutte le funzionalità e vincoli (e.g., security, performance) del sistema desiderato dal customer. <

___

Quale delle seguenti affermazione è vera riguardo al beta testing ?

1) Una release del software è resa disponibile agli utenti (beta users) per permettergli di sperimentare e quindi segnalare eventuali problemi rilevati agli sviluppatori. <
2) Test automatizzato sono eseguiti sulla versione finale del sistema presso il sito di sviluppo del software.
3) Test automatizzato sono eseguiti sulla versione finale del sistema presso il cliente.

___

Una azienda finanziaria desidera costruire un sistema software per ottimizzare i processi di business. Quali delle seguenti attività può contribuire a validare i requisiti del sistema ?

1) Costruire un modello di simulazione per i principali aspetti dei processi di business dell'azienda e per il sistema software da realizzare e valutare le migliorie apportate dal sistema software ai processi di business dell'azienda mediante simulazione. <
2) Costruire un prototipo del sistema e valutarne i requisiti non funzionali usando i dati storici dall'azienda.
3) Costruire un prototipo del sistema e testarlo rispetto ai requisiti funzionali usando i dati storici dall'azienda.

___

Which of the following is an agile principle?

1) Customers should not interfere with the software development.
2) Customers should just provide requirements and verify them when the project is completed.
3) Customers should be closely involved throughout the development process. <

___

Il _branch coverage_ di un insieme di test cases è la percentuale di branch del programma che sono attraversati da almeno un test case.
Si consideri il seguente programma C:
```c
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>
#define N  4    /* number of test cases */
int f(int x1, int x2)
{
  if (x1 + x2 <= 2)
  return (1);
  else return (2);     
}
int main() {    int  i, y;   int x1[N], x2[N];
  // define test cases
    x1[0] = 3; x2[0] = -2;    x1[1] = 4; x2[1] = -3;    x1[2] = 5; x2[2] = -4;    x1[3] = 6; x2[3] = -5; 
    // testing
  for (i = 0; i < N; i++)  {
      y = f(x1[i], x2[i]);       // function under testing
      assert(y ==(x1[i], x2[i] <= 2) ? 1 : 2);   // oracle
    }
   printf("All %d test cases passed\n", N);
    return (0);   
}
```

Il programma main() sopra realizza il nostro testing per la funzione f1(). I test cases sono i valori in x1\[i] ed x2\[i].  
Quale delle seguenti è la branch coverage conseguita?

1) 100%
2) 50% <
3) 80%

___

Il team di sviluppo di un azienda consiste di un senior software engineer e due sviluppatori junior. Usando un approccio agile, ogni iterazione impegna tutti e tre i membri del team per un mese ed occorrono tre iterazioni per completare lo sviluppo. Si assuma che non ci siano "change requests" e che il membro senior costi A Eur/mese ed i membri junior B Eur/mese. Qual'e' il costo dello sviluppo usando un approccio agile ?

1) 3\*(A + 2\*B)
2) A + 2\*B
3) 3\*A + 2\*B <

___

## Esame SE del 2021-03-29 ore 15.00

Quale delle seguenti affermazioni è vera riguardo all'alpha testing ?

1) Test automatizzati sono eseguiti sulla prima release del sistema.
2) Test automatizzati sono eseguiti su una versione preliminare del sistema.
3) Gli utenti del sistema lavorano insieme al team di sviluppo per testare il software nel sito di sviluppo. <

___

Il rischio R può essere calcolato come R = P\*C, dove P è la probabilità dell'evento avverso (software failure nel nostro contesto) e C è il costo dell'occorrenza dell'evento avverso. Assumiamo che la probabilità P sia legata al costo di sviluppo S dalla formula P = exp(-b\*S), dove b è una opportuna costante note da dati storici aziendali. Quale sarà il costo dello sviluppo S di un software il cui costo della failure è C ed il rischio ammesso è R?

1) S = (1/b)\*ln(R/C)
2) S = b\*ln(R/C)
3) S = (1/b)\*ln(C/R) <

___

Il system testing si concentra su:

1) Testare le interfacce per ciascuna componente.
2) Testare l'interazione tra  le componenti del sistema (cioè, integrazione di molte unità di sistema). <
3) Testare le funzionalità di unità software individuali, oggetti, classi o metodi.

___

Quale delle seguenti affermazione è vera riguardo al beta testing ?

1) Test automatizzato sono eseguiti sulla versione finale del sistema presso il sito di sviluppo del software.
2) Test automatizzato sono eseguiti sulla versione finale del sistema presso il cliente.
3) Una release del software è resa disponibile agli utenti (beta users) per permettergli di sperimentare e quindi segnalare eventuali problemi rilevati agli sviluppatori. <

___

 Quali delle seguenti attività può contribuire a validare i requisiti di un sistema ?

1) Costruire un prototipo e valutarne attentamente le performance.
2) Costruire un prototipo, metterlo in esercizio ed accertarsi che i porti i benefici attesi. <
3) Costruire un prototipo e testarlo a fondo per evidenziare subito errori di implementazione.

___

Una azienda vende software utilizzando un contratto di Service Level Agreement (SLA) per cui l'utente paga 1000 Eur al mese di licenza e l'azienda garantisce che il software sia "up and running". Questo vuol dire che failures del software generano un costo (quello del repair). Sia C = 10000 Eur il costo del repair di una failure e R = P*C il valore atteso (rischio) del costo dovuto alle failures (dove P è la probabilità di una software failure). Ovviamente affinché il business sia profittevole deve essere che R sia al più 1000 Eur. Qual'e' il valore massimo di P che garantisce la validità del modello di business di cui sopra ?

1) P=1/10000
2) P = 1/1000
3) P = 1/10 <

___

Una azienda finanziaria desidera costruire un sistema software per ottimizzare i processi di business. Quali delle seguenti attività può contribuire a validare i requisiti del sistema ?

1) Costruire un modello di simulazione per i principali aspetti dei processi di business dell'azienda e per il sistema software da realizzare e valutare le migliorie apportate dal sistema software ai processi di business dell'azienda mediante simulazione. <
2) Costruire un prototipo del sistema e valutarne i requisiti non funzionali usando i dati storici dall'azienda.
3) Costruire un prototipo del sistema e testarlo rispetto ai requisiti funzionali usando i dati storici dall'azienda.

___

Si consideri il Test-Driven Development (TDD). Quale delle seguenti affermazioni è vera?

1) Per ciascun incremento di funzionalità, scrivi test automatizzati, implementa la funzionalità, esegui i test e rivedi l'implementazione come necessario. <
2) Per ciascun incremento di funzionalità, implementa la funzionalità, scrivi test automatizzati, esegui i test e rivedi l'implementazione come necessario.
3) Scrivi test automatizzati per tutti i requisiti di sistema, esegui i test e rivedi l'implementazione come necessario.

___

Si consideri il monitor seguente che ritorna true appena i requisiti per il sistema monitorato sono violati.
```c
block Monitor  
input Real x;    
output Boolean y;
Boolean w;  
initial equation  
y = false;
equation  
w = ((x < 0) or (x > 5));  
algorithm  
when edge(w) then  
y := true;
end when;
end Monitor;
```

Quale delle seguenti affermazioni meglio descrive il requisito monitorato.

1) La variabile x è nell'intervallo \[0, 5]. <
2) La variabile x è fuori dall'intervallo \[0, 5].
3) La variable x è minore di 0.

___

Un azienda ha un team di sviluppo in cui il 90% dei membri è junior (cioè con poca esperienza) ed il 10% è senior (cioè con molta esperienza).  Con l'obiettivo di massimizzare il numero di progetti completati nell'unità di tempo, quale dei seguenti modelli di sviluppo software appare più opportuno.

1) Plan driven <
2) Basato sul riuso
3) Iterativo

___

Si consideri un software sviluppato seguendo un approccio iterativo implementato con due fasi: F1 seguita da F2. Ciascuna fase ha costo A. Con probabilità p potrebbe essere necessario ripetere F1 una seconda volta.  Con probabilità q potrebbe essere necessario ripetere F2 una seconda volta. Qual'e' il costo atteso dello sviluppo dell'intero software?

1) A\*(2 + p +q) <
2) A\*(1 + p +q)
3) A\*(3 + p +q)

___

Si consideri un software sviluppato seguendo un approccio plan-driven implementato con tre fasi: F1, F2, F3. Le "change requests"  arrivano con probabilità p dopo ciascuna fase e provocano la ripetizione (con relativo costo) di tutte le fasi che precedono. Quali delle seguenti catene di Markov modella lo sviluppo software descritto.

![|700](https://i.imgur.com/xe3lMi6.png)

- La risposta giusta è la 3

___

Un processo di sviluppo agile consiste di 3 iterazioni identiche di costo A. Alla fine di ogni iterazione vengono prese in considerazione le "change requests" e, se ve ne sono, l'iterazione viene ripetuta. Sia p la probabilità che ci siano "change requests" all fine di una iterazione. Il valore atteso del costo del progetto è:

1) 3\*(1 + p)\*A <
2) 3\*p\*A
3) 3\*(A + p)

___

Quale delle seguenti affermazioni è vera riguardo al performance testing?

1) Il performance testing è tipicamente eseguito solo sulle componenti del sistema prima dell'integrazione.
2) Il performance testing è tipicamente eseguito su un prototipo del sistema.
3) Il performance testing è tipicamente eseguito una volta che il sistema è stato completamento integrato. <

___

Si consideri un software costituito da due fasi F1 ed F2 ciascuna di costo A. Con probabilità p la fase F1 deve essere ripetuta (a causa di change requests) e con probabilità (1 - p) si passa alla fase F2 e poi al completamento (End) dello sviluppo. Qual'eè il costo atteso per lo sviluppo del software seguendo il processo sopra descritto ?

1) A\*(1 + p)
2) 3\*A\*p
3) A\*(2 + p) <

___

Quale delle seguenti frasi meglio descrive il criterio di "requirements verifiability" che è parte della "requirements validation activity".

1) Per ciascun requisito, dovremmo essere in grado di scrivere un insieme di test che può dimostrare che il sistema sviluppato soddisfa il requisito considerato. <
2) Per ciascuna coppia di componenti, dovremmo essere in grado di scrivere un insieme di test che può dimostrare che l'interazione tra le componenti soddisfa tutti i requisiti di interfaccia.
3) Per ciascuna componente del sistema, dovremmo essere in grado di scrivere un insieme di test che può dimostrare che essa soddisfa tutti i requisiti.

___

Una azienda manifatturiera desidera costruire un sistema software per monitorare (attraverso sensori) la produzione al fine di ridurre gli scarti. Quali delle seguenti attività contribuisce a validare i requisiti del sistema.

1) Costruire un prototipo, eseguirlo usando dati storici dai log di produzione e valutare la capacità del prototipo di ridurre gli scarti. <
2) Costruire un prototipo, eseguirlo usando dati storici dai log di produzione ed identificare errori di implementazione.
3) Costruire un prototipo, eseguirlo usando dati storici dai log di produzione e valutarne le performance.

___

Si pianifica lo sviluppo di un sistema software per controllare il sistema di anti-lock braking in un automobile. Quale dei seguenti è il tipico processo software usato per questo tipo di sistema software ?

1) Sviluppo Plan-driven. <
2) Sviluppo Iterativo.
3) Extreme programming.

___

Focalizzandosi sui metodi agile di sviluppo del software, quale delle seguenti affermazioni è vera?

1) Per evitare di sprecare tempo durante la fase di sviluppo del software, il customer non è mai coinvolto nel processo di sviluppo del software.
2) Le attività di definizione dei requisiti e di sviluppo sono interleaved. <
3) Per evitare di sprecare tempo durante la fase di sviluppo del software, questa inizia solo quando i requisiti sono stati completamente definiti.

___

Quale delle seguenti affermazioni è vera riguardo ai metodi agile ?

1) I metodi agile sono metodi di sviluppo orientato al riuso.
2) I metodi agile sono metodi di sviluppo plan-driven.
3) I metodi agile sono metodi di sviluppo incrementale. <

___

Si consideri un software sviluppato seguendo un approccio plan-driven implementato con tre fasi: F1, F2, F3. Dopo ogni fase c'e' una probabilità p di dover ripeter la fase precedente ed una probabilità (1 - p) di passare alla fase successiva (sino ad arrivare al termine dello sviluppo). Quale delle seguenti catene di Markov modella il processo software descritto sopra?

![|700](https://i.imgur.com/Y4wlEhu.png)

- La risposta giusta è la 2

___

Il team di sviluppo di un azienda consiste di un senior software engineer e due sviluppatori junior. Usando un approccio plan-driven (ad esempio, water-fall) la fase di design impegna solo il membro senior per tre mesi e la fase di sviluppo e testing solo i due membri junior per tre mesi. Si assuma che non ci siano "change requests" e che il membro senior costi A Eur/mese ed i membri junior B Eur/mese. Qual'e' il costo dello sviluppo usando un approccio plan-driven come sopra ?

1) 3\*A + 6\*B <
2) A + 2\*B
3) 3\*A + 3\*B

___

Si consideri un software sviluppato seguendo un approccio iterativo implementato con due fasi: F1 seguita da F2. Ciascuna fase ha costo A e deve essere ripetuta una seconda volta con probabilità p. Qual'e' il costo atteso dello sviluppo dell'intero software?

1) 3\*A\*(p + 1)
2) 2\*A\*(p + 2)
3) 2\*A\*(p +1) <

___

Un processo di sviluppo agile consiste di varie iterazioni. Alla fine di ogni iterazione vengono prese in considerazione le "change requests" e, se ve ne sono, l'iterazione viene ripetuta. Sia p la probabilità che ci siano "change requests" all fine di una iterazione e sia A il costo di una iterazione. Il valore atteso del costo per l'iterazione è:

1) A
2) (1 + p)\*A <
3) p\*A

___

Si consideri il monitor seguente che ritorna true appena il sistema viola il requisito monitorato.
```c
block Monitor
input Real x;  
output Boolean y;
Boolean w;
initial equation
y = false;
equation
w = ((x < 1) or (x > 4)) and ((x < 15) or (x > 20));
algorithm
when edge(w) then
y := true;
end when;
end Monitor;
```

Quale delle seguenti affermazioni meglio descrive il requisito monitorato?

1) La variabile x è nell'intervallo \[1, 4] oppure nell'intervallo \[15, 20]. <
2) La variabile x è nell'intervallo \[1, 4] e fuori dall'intervallo \[15, 20].
3) La variabile x è fuori dall'intervallo \[1, 4] e fuori dall'intervallo \[15, 20].

___

"Ogni giorno, per ciascuna clinica, il sistema genererà una lista dei pazienti che hanno un appuntamento quel giorno."
La frase precedente è un esempio di:

1) Requisito non-funzionale.
2) Requisito di performance.
3) Requisito funzionale. <

___

La validazione risponde alla seguenete domanda:

1) Stiamo costruendo il sistema giusto ? <
2) Stiamo costruendo il sistema nel modo giusto ?
3) Sono soddisfatti i requisti funzionali ?

___

Unit testing si concentra su:

1) Testare le interfacce di ciascuna componente.
2) Testare l'interazione tra componenti.
3) Testare funzionalità di unità software individuali, oggetti, classi o metodi. <

___

Quali delle seguenti attività è parte del processo di validazione dei requisiti ?

1) Accertarsi che il sistema soddisfi i requisiti dati.
2) Accertarsi che i requisiti definiscano un sistema che risolve il problema che l'utente pianifica di risolvere. <
3) Accertarsi che l'architettura del sistema soddisfi i requisiti dati.

___

Un processo di sviluppo plan-driven consiste di 2 fasi F1, F2, ciascuna costo A. Alla fine di ogni fase vengono prese in considerazione le "change requests" e, se ve ne sono, lo sviluppo viene ripetuto a partire dalla prima iterazione.  Quindi con nessuna change request si hanno le fasi: F1, F2 e costo 2A. Con una "change request" dopo la prima fase si ha: F1, F1, F2 e costo 3A.  Con una change request dopo la fase 2 si ha: F1, F2, F1, F2 e costo 4A. Qual'è il costo nel caso in cui ci siano change requests sia dopo la fase 1 che dopo la fase 2.

1) 7\*A
2) 6\*A
3) 5\*A <

___

Il team di sviluppo di un azienda consiste di un senior software engineer e due sviluppatori junior. Usando un approccio agile, ogni iterazione impegna tutti e tre i membri del team per un mese ed occorrono tre iterazioni per completare lo sviluppo. Si assuma che non ci siano "change requests" e che il membro senior costi A Eur/mese ed i membri junior B Eur/mese. Qual'e' il costo dello sviluppo usando un approccio agile ?

1) 3\*A + 2\*B
2) A + 2\*B
3) 3\*(A + 2\*B) <

___

Il component testing si concentra su:

1) Testare le interfacce per ciascun componente. <
2) Testare funzionalità di unità software individuali, oggetti, classi o metodi.
3) Testare l'interazione tra molte componenti (cioè integrazione di molte unità).

___

## Esame SE (Tronci) del 09-06-2021

Si consideri il Test-Driven Development (TDD). Quale delle seguenti affermazioni è vera?

1) Scrivi test automatizzati per tutti i requisiti di sistema, esegui i test e rivedi l'implementazione come necessario.
2) Per ciascun incremento di funzionalità, scrivi test automatizzati, implementa la funzionalità, esegui i test e rivedi l'implementazione come necessario. <
3) Per ciascun incremento di funzionalità, implementa la funzionalità, scrivi test automatizzati, esegui i test e rivedi l'implementazione come necessario.

___

Quale delle seguenti affermazioni è vera riguardo all'alpha testing ?

1) Test automatizzati sono eseguiti su una versione preliminare del sistema.
2) Test automatizzati sono eseguiti sulla prima release del sistema.
3) Gli utenti del sistema lavorano insieme al team di sviluppo per testare il software nel sito di sviluppo. <

___

Si pianifica lo sviluppo di un sistema software per controllare il sistema di anti-lock braking in un automobile. Quale dei seguenti è il tipico processo software usato per questo tipo di sistema software ?

1) Extreme programming.
2) Sviluppo Plan-driven. <
3) Sviluppo Iterativo.

___

Il rischio R può essere calcolato come R = P\*C, dove P è la probabilità dell'evento avverso (software failure nel nostro contesto) e C è il costo dell'occorrenza dell'evento avverso. Si consideri un software il cui costo per la failure è C = 1000000 EUR. Volendo un rischio non superiore a 1000 EUR quale è il valore massimo della probabilità di failure P accettabile?

1) 1/10
2) 1/1000 <
3) 1/100

___

Si consideri un software costituito da due fasi F1 ed F2 ciascuna di costo A. Con probabilità p la fase F1 deve essere ripetuta (a causa di change requests) e con probabilità (1 - p) si passa alla fase F2 e poi al completamento (End) dello sviluppo. Qual'eè il costo atteso per lo sviluppo del software seguendo il processo sopra descritto ?

1) A\*(1 + p)
2) 3\*A\*p
3) A\*(2 + p) <

___

Si consideri un software sviluppato seguendo un approccio plan-driven implementato con tre fasi: F1, F2, F3 ciascuna con costo A. Le "change request" possono arrivare solo al fine di una fase e provocano la ripetizione (con relativo costo) di tutte le fasi che precedono. Si assuma che dopo la fase F3 (cioè al termine dello sviluppo) arriva una change request. Qual'e' il costo totale per lo sviluppo del software in questione.

1) 4\*A
2) 5\*A
3) 6\*A <

___

Consider reuse-based software development. Which of the following is true?

1) Development and integration are not needed thanks to reuse.
2) Requirements specification precedes the component analysis activity. <
3) Requirements specification is not needed thanks to reuse.

___

Il rischio R può essere calcolato come R = P\*C, dove P è la probabilità dell'evento avverso (software failure nel nostro contesto) e C è il costo dell'occorrenza dell'evento avverso. Assumiamo che la probabilità P sia legata al costo di sviluppo S dalla formula P = exp(-b\*S), dove b è una opportuna costante note da dati storici aziendali. Quale sarà il costo dello sviluppo S di un software il cui costo della failure è C ed il rischio ammesso è R?

1) S = (1/b)\*ln(R/C)
2) S = (1/b)\*ln(C/R) <
3) S = b\*ln(R/C)

___

Quale delle seguenti affermazione è vera riguardo al beta testing ?

1) Test automatizzato sono eseguiti sulla versione finale del sistema presso il sito di sviluppo del software.
2) Test automatizzato sono eseguiti sulla versione finale del sistema presso il cliente.
3) Una release del software è resa disponibile agli utenti (beta users) per permettergli di sperimentare e quindi segnalare eventuali problemi rilevati agli sviluppatori. <

___

Si consideri un software sviluppato seguendo un approccio iterativo implementato con due fasi: F1 seguita da F2. Ciascuna fase ha costo A e deve essere ripetuta una seconda volta con probabilità p. Qual'e' il costo atteso dello sviluppo dell'intero software?

1) 3\*A\*(p + 1)
2) 2\*A\*(p + 2)
3) 2\*A\*(p +1) <

___

Quale delle seguenti affermazioni è vera riguardo al performance testing?

1) Il performance testing è tipicamente eseguito una volta che il sistema è stato completamento integrato. <
2) Il performance testing è tipicamente eseguito solo sulle componenti del sistema prima dell'integrazione.
3) Il performance testing è tipicamente eseguito su un prototipo del sistema.

___

Si consideri un software sviluppato seguendo un approccio iterativo implementato con tre fasi: F1, F2, F3. Ciascuna fase ha costo A. Qual'e' il costo dello sviluppo dell'intero software?

1) 3\*A <
2) A
3) 2\*A

___

Si consideri il seguente requisito: "Il sistema fornisce l'elenco dei clienti in ordine alfabetico". Di che tipo di requisito si tratta?

1) Requisito di sistema.
2) Requisito non-funzionale.
3) Requisito utente. <

___

Il system testing si concentra su:

1) Testare l'interazione tra  le componenti del sistema (cioè, integrazione di molte unità di sistema). <
2) Testare le interfacce per ciascuna componente.
3) Testare le funzionalità di unità software individuali, oggetti, classi o metodi.

___

Si consideri un software sviluppato seguendo un approccio plan-driven implementato con due fasi: F1, F2. La fase F1 ha costo A e la fase F2 ha costo il 50% di A. Qual'e' il costo dello sviluppo del software?

1) 1.5\*A <
2) A
3) 0.5\*A

___

Si pianifica di sviluppare un software gestionale per una università. Considerando che questo può essere considerato un sistema mission-critical, quali dei seguenti modelli di processi software generici è più adatto per lo sviluppo di tale software.

1) Sviluppo plan-driven. <
2) Sviluppo Iterativo.
3) Sviluppo Agile.

___

Unit testing si concentra su:

1) Testare le interfacce di ciascuna componente.
2) Testare l'interazione tra componenti.
3) Testare funzionalità di unità software individuali, oggetti, classi o metodi. <

___

Il component testing si concentra su:

1) Testare l'interazione tra molte componenti (cioè integrazione di molte unità).
2) Testare funzionalità di unità software individuali, oggetti, classi o metodi.
3) Testare le interfacce per ciascun componente. <

___

Un azienda ha un team di sviluppo in cui il 90% dei membri è junior (cioè con poca esperienza) ed il 10% è senior (cioè con molta esperienza).  Con l'obiettivo di massimizzare il numero di progetti completati nell'unità di tempo, quale dei seguenti modelli di sviluppo software appare più opportuno.

1) Plan driven
2) Basato sul riuso
3) Iterativo

## Domande 2025

Quale delle seguenti frasi meglio descrive l'obiettivo del "check di consistenza" che è parte della "requirements validation activity".

1) Assicurarsi che non ci siano requisiti in conflitto con altri requisiti. <
2) Assicurarsi che per ogni requisito esista un insieme di test che lo possa verificare.
3) Assicurarsi che i requisiti funzionali descrivano tutte le funzionalità del sistema.

___

Quale delle seguenti frasi meglio descrive l'obiettivo del "validity check" che è parte della "requirements validation activity".

1) Assicurarsi che i requisiti funzionali descrivano tutte le funzionalità del sistema.
2) Assicurarsi che non ci siano requisiti in conflitto con altri requisiti.
3) Assicurarsi che un sistema che soddisfa i requisiti risolve il problema del "customer". <

___

Quale delle seguenti frasi meglio descrive l'obiettivo del "check di completezza" che è parte della "requirements validation activity".

1) Assicurarsi che per ogni requisito sia stato implementato nel sistema.
2) Assicurarsi che i requisiti funzionali descrivano tutte le funzionalità del sistema.
3) Assicurarsi che i requisisti descrivano tutte le funzionalità e vincoli (e.g., security, performance) del sistema desiderato dal customer. <

___

Quale delle seguenti frasi meglio descrive il criterio di "requirements verifiability" che è parte della "requirements validation activity".

1) Per ciascun requisito, dovremmo essere in grado di scrivere un insieme di test che può dimostrare che il sistema sviluppato soddisfa il requisito considerato. <
2) Per ciascuna coppia di componenti, dovremmo essere in grado di scrivere un insieme di test che può dimostrare che l'interazione tra le componenti soddisfa tutti i requisiti di interfaccia.
3) Per ciascuna componente del sistema, dovremmo essere in grado di scrivere un insieme di test che può dimostrare che essa soddisfa tutti i requisiti.

___

L'attività di _unit testing_ di una funzione è stata suddivisa nei seguenti task:

|Task identifier|Task description|
|---|---|
|TDEF|Definition of test cases|
|TORC|Definition of test oracle|
|TEXE|Esecuzione dei casi di test|
|TVAL|Valutazione dei casi di test|

Quale dei seguenti insiemi di vincoli di precedenza (dove A < B significa che A precede B) deve necessariamente valere, considerata la descrizione data dei tasks?

1) TEXE < TVAL, TDEF < TEXE, TORC < TVAL. <
2) TVAL < TEXE, TORC < TDEF, TORC < TVAL.
3) TEXE < TORC, TVAL < TEXE, TVAL < TORC.

4) TVAL < TEXE, TEXE < TDEF, TVAL < TORC.
5) TVAL < TEXE, TORC < TDEF, TVAL < TORC.

___

Una azienda vende software utilizzando un contratto di Service Level Agreement (SLA) per cui l'utente paga 1000 Eur al mese di licenza e l'azienda garantisce che il software sia "up and running". Questo vuol dire che failures del software generano un costo (quello del repair). Sia C = 10000 Eur il costo del repair di una failure e R = P*C il valore atteso (rischio) del costo dovuto alle failures (dove P è la probabilità di una software failure). Ovviamente affinché il business sia profittevole deve essere che R sia al più 1000 Eur. Qual'e' il valore massimo di P che garantisce la validità del modello di business di cui sopra ?

1) P=1/10000
2) P = 1/1000
3) P = 1/10 <

_Basta fare_ P=R/C ovvero 1000/10000 = 1/10
___

La formula per calcolare il costo di iterazioni è

Quanti stati minimi per finire \* (1 + probabilità di ripetizione di questa fase) \* costo di questa fase

cioè: 3\*(1 + p)\*A

se lo sviluppo consiste in 3 fasi di costo uguale e stessa probabilità di ripetersi


___

Quale dei seguenti è un requisito non funzionale?

1) L'output del sistema è sempre una matrice simmetrica.
2) Il tempo di esecuzione del sistema è inferiore al minuto. <
3) L'output del sistema è sempre una potenza di 2.

___

Quale dei seguenti è un requisito non funzionale?

1) L'output del sistema è sempre una matrice invertibile.
2) L'utilizzo della RAM è sempre inferiore ai 4GBytes. <
3) L'output del sistema è sempre un vettore ordinato.

_Quindi_ se c'è scritto _output_ allora è funzionale (forse)
___

Per testare un sistema si vuole costruire un generatore che ogni T secondi invia un valore v a sistema da testare. 

Per ogni invio, il valore T è un valore intero scelto uniformemente a random nell'interallo \[20, 30] mentre il valore v è un valore scelto aggiungendo, uniformemete a random, il valore -1 o +1 al valore precedente di v. Il valore iniziale di v è 0.  

Quale dei seguenti programmi meglio definisce il generator di cui sopra?

```c
main{

srand(time(NULL));

v = 0;  

while (1)  {

send _value_to_system_under_testing(v);  

T = 20 + rand()%11; <------------------------------------- 11 e non 10

sleep(T);

v = v -1 + 2*rand()%2;  <-------------------- v = v ..... e non v = ...........

}  // while  

}  // main()
```

___

Per testare un sistema si vuole costruire un generatore che ogni T secondi invia un valore v a sistema da testare. 

Per ogni invio, il valore T è un valore intero scelto uniformemente a random nell'interallo \[1, 10] mentre il valore v è un valore intero scelto uniformemente  a random nel'intervallo [0, 1].

Quale dei seguenti programmi meglio definisce il generator di cui sopra?

```c
main{

srand(time(NULL));

while (1)  {

v = rand()%2;

send _value_to_system_under_testing(v);  

T = 1 + rand()%10; <-------------------------------- 1 + rand e non solo rand

sleep(T);  

}  // while  

}  // main()
```