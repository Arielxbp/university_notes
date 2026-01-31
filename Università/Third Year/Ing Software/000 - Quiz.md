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



