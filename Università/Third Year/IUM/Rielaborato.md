___

L'interazione uomo-macchina è un campo multi-disciplinare interessato al:
- Design, valutazione e implementazione di sistemi informatici interattivi adatti all'uso umano.

L'obiettivo del HCI è quello di avere sistemi che supportano il compito (__task__) dell'utente, focalizzandosi sulla __usabilità__ della macchina, ovvero:
- Dato un utente, il suo compito che deve compiere e un computer, tale macchina deve aiutare l'utente rendendosi utile, essere usabile ed essere usato.


In Human-Computer Interaction (HCI), an

**artifact** (or _artefact_) is ==any object, tool, or byproduct created or modified by human workmanship during the design and development process==.
Artifacts are typically categorized by their role in the project lifecycle:

- **Research Artifacts:** Objects that capture insights about users, such as User Personas, empathy maps, and User Journey Maps.
- **Design Artifacts:** Tangible representations of a solution, including Wireframes, mockups, and sitemaps.
- **Cognitive Artifacts:** Artificial devices (physical or digital) that maintain or display information to enhance human cognitive performance, such as calendars, calculators, or to-do lists.
- **Testing & Validation Artifacts:** Evidence gathered from user interaction, such as usability test reports, A/B test results, and Prototypes.
- **Speculative Artifacts:** Design "probes" or objects meant to provoke debate about future ethical or social impacts of technology, rather than for immediate use.

Di seguito si elencano alcuni __approcci__ per modellare un processo di design.

## User Centered Design (USD)

Un design centrato sull'utente prende i bisogni, le richieste e le limitazioni dell'utente finale effettivo  
in considerazione durante ogni fase del processo di design.

Questo porta a benefici:
- Il sistema diventa più facile da capire.
- Il sistema diventa più performante.
- Il sistema porterà a meno errori da parte degli utenti.
## Participatory Design

È USD ma dove gli utenti sono direttamente coinvolti in un design collaborativo sulle cose e applicazioni che usano.

## Agile Interaction Design

Il sistema è costruito in modo __incrementale__ in rapidi cicli di rilascio.

Ovviamente questa rapidità si riflette anche nella realizzazione di __prototipi__ e nella tecnica di realizzazione. I prototipi realizzati sono molto economici da realizzare.

# Interfacce

Un interfaccia è un __posto__ dove sistemi indipendenti e non correlati si incontrano per communicare (__interagire__) tra di loro.

L'interfaccia utente nell'interazione uomo-macchina è lo spazio dove avviene l'interazione fra uomo e macchina.

L'obiettivo di tale interazione è il permettere all'uomo di effettuare operazioni e controllare la macchina grazie alle informazioni che quest'ultima "dice" all'operatore che lo sta usando.

L'interfaccia utente include sia:
- Elementi hardware, ovvero fisici.
- Elementi software, ovvero logici.

L'interfaccia utente provvede:
- Degli input, che permettono all'utente di manipolare un sistema.
- Degli output, che permettono al sistema di indicare gli effetti della manipolazione fatta dall'utente.

## Storia delle macchine computabili

-

## Storia delle interfacce

Il __Memex__ di Vannevar Bush ($1945$) è stato un sistema di __proto-hypertext__, cioè un dispositivo elettromeccanico per leggere una grande quantità di informazioni, e collegarle tramite links e appunti (notes).

Lo __Sketchpad__ di Ivan Sutherland ($1963$) è un primo esempio di __interfaccia utente grafica__ (GUI), in quanto usava un CRT e una penna per disegnarci sopra.

## WIMP e Post-WIMP (Window, Icon, Menu, Pointer)

L'acronimo WIMP sta ad indicare:
- Window.
- Icon.
- Menu.
- Pointer.

Questi sono le interfacce principali usate maggiormente adesso.

Esistono tuttavia altri tipi di interfacce (Post-WIMP), come:
- Sistemi VR (Virtual reality).
- Interfacce basate sulla voce.
- Movimenti delle mani. (E.g. Sensori che rilevano i movimenti delle mani)
- Controlli fisici (Physical controls). (Touch screens?)
- Interfacce utente tattili (E.g. Guanto che detecta i movimenti della mano)

## Personas

È uno strumento usato nel design di interfacce.

Una "persona" rappresenta un modello __astratto__ di utenti reali, create sulla base di dati ottenuti tramite il needfinding e l'analysis.

Aiutano a comprendere meglio i need e i comportamenti degli utenti durante il processo di progettazione.

Forniscono un quadro di riferimento per la progettazione, consentendo di identificare le esigenze degli utenti e le possibili sfide.

È tipo un CV ma con:
- Nome
- __Una foto__.
- Caratteristiche demografiche, tipo l'età, il sesso, la professione, ...
- Frustrazioni, ovvero quali sono i problemi che potrebbe sperimentare.
- Comportamenti, ovvero come utilizza il sistema, quali sono le sue abitudini.

# Human-Centered Design Process

![|500](https://i.imgur.com/oaaR8en.png)

I passi principali del processo di design centrato sull'utente sono:
- __Needfinding__: cosa esattamente è necessario, come le persone attualmente compiono questo obiettivo.
- __Analysis__: formalizzare e strutturare i bisogni degli utenti, creare le task.
- __Design__: creare il sistema, le regole, le linee guida e i principi di design da seguire.
- __Iteration and prototyping__, __evaluation__: il design deve essere supportato da un immediata verifica, dove si valuta il design nella sua forma parziale. Ciò coinvolge ovviamente gli utenti finali.
- __Implementation and deployment__: solo dopo aver valutato il design si procede all'implementazione fisica (Hardware) e logica (Software), insieme alla documentazione.

# Needfinding


> [!NOTE] Obiettivo
> Capire i requisiti del sistema e i bisogni degli utenti.

Il Needfinding è il processo usato per:
- Scoprire opportunità tramite il riconoscimento di lacune di un sistema.

Tali lacune sono detti bisogni (o __needs__).

Quindi il Needfinding equivale a:
- Trovare i bisogni di un potenziale utente.
Ciò comporta inoltre il sapere:
- Chi sono gli utenti.
- Come stanno facendo quei bisogni attualmente.
- In che contesto lo stanno facendo.

## Conoscere i tuoi utenti

I designer e i developer posseggono conoscenze, skills e altro che sono principalmente diversi da quelli dei tuoi utenti.

Stessa cosa vale per il cliente che chiede un sistema.

Serve quindi comunicare e interagire direttamente con gli utenti finali in modo concreto:
- Attraverso interviste, questionari, partecipazioni dell'utente.
- Osservarli, segnandosi in un `log` (diario) o registrando video.
- Analizzare i loro movimenti e azioni.
- Discutere con gli utenti le scoperte fatte tramite l'osservazione.
	- Chiedere il perché ha compiuto una certa azione.

## Tecniche adottate nel Needfinding

I metodi per eseguire il needfinding sono:
- Osservazione, ricerca etnografica.
- Diari.
- Interviste.
- Gruppi scelti manualmente.
- Questionari.

### Osservazione

L'osservazione serve a:
- __Individuare necessità__ (needs).
- Comprendere i loro obiettivi.
- Identificare problemi esistenti.

Un osservazione etnografica ha come obiettivo quello di ottenere i dati necessari a influenzare una redesign dell'interfaccia.

Comporta l'ascoltare e l'osservare attentamente gli utenti, complementando attraverso appunti e registrazioni video/audio.

Esistono vari tipi di osservazione:
- __Osservazione controllata__, quindi all'interno di un ambiente controllato.
- __Osservazione naturalistica__, quindi all'esterno, in modo "naturale".

#### Osservazione controllata

L'osservazione controllata è:
- Facile da __riprodurre__, in quanto è possibile ottenere risultati simili ripetendol'osservazione.
- Facile da __analizzare__, i dati quantitativi richiedono meno sforzo da analizzare rispetto a dati qualitativi.
- __Veloce__ da condurre, il recruitamento potrebbe prendere del tempo, ma l'osservazione controllata è piuttosto facile da eseguire.

Comporta però un effetto collaterale non sempre voluto, il __Hawthorne Effect__:
- Cioè l'atto di osservare come qualcuno fa qualcosa __può__ cambiare il loro approccio a come fanno quella cosa.

#### Osservazione naturalistica

L'osservazione naturalistica è:
- Più __affidabile__, in quanto gli utenti quando usano un prodotto interagendo quotidianamente producono comportamenti più realistici, rispetto al seguire delle istruzioni in un laboratorio.
- Più __utile per idee__, in quanto una ricerca __qualitativa__ può generare molte idee per migliorare il prodotto in quanto porta a più possibili scenari rispetto ad una ricerca quantitativa.

Però tale osservazione è:
- Difficile ottenere delle quantità rappresentative, cioè ognuno potrebbe avere un'esperienza totalmente diversa, portando a molteplici osservazioni totalmente unici. Quindi non si riesce a trarre un punto centrale sulla quale concentrarsi.
- Più difficile da replicare.
- Difficile manipolare __variabili esterne__. Per esempio un utente si comporta in modo diverso quando piove rispetto a quando è soleggiato mentre cammina con il prodotto.

#### Blending in

Durante l'osservazione l'osservatore può adottare due metodi:
- Diventare un osservatore esterno, quindi non interagisce in alcun modo durante l'osservazione.
- Diventare un osservatore "partecipante" interno.

### Diari

I diari sono usati per eseguire il needfinding se:
- Il periodo di osservazione è lungo.

L'osservare l'utente per lunghi periodi di tempo in molti posti non è fattibile per un osservatore, quindi si usano questi diari.

Il diario è un'utensile (tools) che richiede l'utente di prendere appunti delle loro azioni, ciò può avvenire:
- Quando effettuano una __azione specifica__.
- In intervalli di tempo prestabiliti.

Questo metodo richiede motivazioni più forti come incentivi per essere effettuato.

### Interviste

Esistono due tipi principali di interviste:
- Interviste di persona.
- Questionari.

#### Utenti intervistati

Gli utenti intervistati dovrebbero essere scelti come rappresentanti di un target di utenti, questi inoltre:
- Sono utenti attuali di un sistema simile al prodotto sulla quale si vuole fare needfinding.
- Possono essere utenti generici se il proprio prodotto è __nuovo__.

Le interviste specifiche sono fatte a:
- Lead users.
- Extreme users.
- Esperti.

L'esecuzione delle interviste deve essere fatto in un tempo e un posto __confortabile__ per l'intervistato.

L'intervista non deve essere un test:
- Chi intervista deve presentarsi, spiegando inoltre lo scopo dell'intervista.
- "You are not testing them, they are helping you".

Evitare domande:
- La cui risposta è scontata.
- Che contengono la risposta.
- __Troppo generiche__.
- __Basate su scenari ipotetici__.
- Che chiedono __quanto spesso__ (domande di frequenza)
- Che cominciano con "__ti piacerebbe__" o "__useresti__"

##### Lead user

I lead users sono gli utenti che hanno dei need __nuovi__, prima di tutti gli altri.
Essi sono particolarmente competenti e sofisticati, solitamente trovano da soli soluzioni ai loro need in quanto beneficiano significativamente da tali soluzioni.

Grazie a questo questo tipo di utenti ci indicano i need che molti avranno nel prossimo futuro.

##### Extreme user

Gli extreme users sono gli utenti che spingono un sistema esistente all'estremo.

Quindi trovano problemi altrimenti difficili da individuare, amplificano i problemi causati dai need e quindi le soluzioni sono più evidenti se studiati.

I loro needs sono quindi i needs anche di altri, ma più evidenti e visibili.

##### Esperti

Gli esperti sono quei utenti che sono del settore.

Possono discutere anche di problemi difficili quando intervistati.



### Questionari

La scala di __Likert__, ovvero da 1 a 5, o da 1 a 7, o da 1 a 9.
I valori agli estremi sono raramente scelti.
Servono per chiedere il livello di agreement about a statement.
Un numero pari di valori tolgono l'uso di un valore come risposta neutrale.

# Task Analysis

## Need

A need is the underlying problem (gap).

## Goal

A goal is the end-state a user wants to achieve.

It describes what the user want to do.

## Task

A task is a set of activities or __sequential steps__ required to achieve a specific __goal__.

Tasks break down the goal into multiple simple pieces.

# Storyboard

Gli storyboard sono delle rappresentazioni grafiche del sistema viste in modo molto basilare, __senza include alcuna funzionalità del sistema__.

Serve a comunicare cosa un utente può ottenere usando il sistema.

Ogni pannello dovrebbe contenere cosa succede __nei punti chiave__ nel tempo.

Le storyboard sono usate sui __tasks__:
- Illustrano un __goal__ per il task.
- Come un task si esegue in vari step.
- Alla fine, come l'utente raggiunge il goal.

Non si deve includere l'interfaccia dell'utente in modo dettagliato. No problemi sul come fare l'interfaccia, buttons, layout, ...

Non si deve perdere tanto tempo sul fare la storyboard. No distrazioni sul voglio farlo troppo bene, porta a voler fare tutto nei minimi dettagli, fonts, colori, icone, ...

Una storyboard __mostra un sistema__ e __il suo contesto d'uso__.

Permette di condividerlo con altri, non lega il sistema a un'interfaccia particolare.
Permette la discussione e il miglioramento delle scelte.

__RIVEDERE COSA NON INCLUDERE NELLE STORYBOARDS__

# Evaluation (valutazione)

La valutazione serve a testare:
- L'__usabilità__ e la __funzionalità__ del sistema.

Può essere eseguita in:
- Un laboratorio.
- Campo aperto.

La valutazione viene eseguita sia sul __design__ che sull'__implementazione__.

I goals della valutazione sono:
- Quello di controllare quanto funzionano le funzionalità del sistema.
- Quello di controllare che effetti provoca l'interfaccia del sistema sull'utente.
- Quello di identificare problemi specifici.

Lo scenario descrive una situazione potenzialmente reale nella quale si immedesimano i partecipanti alla valutazione.

## Metodi per osservare

I metodi usati per osservare la valutazione:
- __Think aloud__.
- __Cooperative evaluation__.
- __Protocol analysis__.
- __Post-task walkthrough__.

### Think aloud

L'utente viene osservato mentre effettua la task e gli viene chiesto di __descrivere__ cosa sta facendo e perché, cosa sta pensando, ...

I vantaggi sono:
- Semplice da fare.
- Può portare a intuizioni utili.
- Può mostrare come il sistema viene usato veramente.

Gli svantaggi sono:
- È soggettivo.
- L'atto di descrivere e parlare e ... può alterare cosa farebbe senza queste richieste.

### Cooperative evaluation

È una variazione del Think aloud.

L'utente collabora insieme al valutatore, si chiedono domande utili a vicenda.

### Protocol analysis

Usare mezzi audio, video, penna e fogli per segnare tutti i passi, pensieri, ...

È un metodo difficile da eseguire con successo.

### Post-task walkthrough

La trascrizione testo/audio/video viene fatta visionare al partecipante per __ottenere dei commenti sul perché__ ha fatto certe cose.

Se è immediato, il partecipante si ricorda ancora il perché ha fatto quella cosa.
Se viene fatto vedere dopo, il partecipante ha avuto tempo per __pensare__.

È necessario nei casi in cui il think aloud non è possibile.

## Esperimenti

Gli esperimenti si fanno scegliendo l'ipotesi, le variabili dipendenti e indipendenti. (più semplici possibili le variabili indipendenti)
Si scelgono i partecipanti e si sceglie il __metodo dell'esperimento__:
- Between subjects.
- Within subjects.

### Between subjects

L'esperimento si fa su una variabile indipendente modificata rispetto alla condizione di controllo (default).

Ogni partecipante __esegue una sola volta__ il test, quindi ha una sola condizione cambiata.

Tale metodo __non risente__ del "__trasferimento dell'apprendimento__".

### Within subjects

A ogni partecipante vengono dati tutte le condizioni dell'esperimento.
Quindi ogni partecipante __svolge più test__.

Questo metodo usa meno gente, cioè meno costoso.

Tale metodo __risente__ del "trasferimento dell'apprendimento".



While Agile focuses on building software through rapid, iterative delivery, UCD ensures that what is being built actually solves the right problems for the end user

## Tecniche di valutazione: Expert-based

Nel progetto solo una o la seconda è realizzabile.
Ogni volta che realizza una versione del prototipo usare una di queste due tecniche.

### Cognitive walkthrough

Per usare cognitive walkthrough serve specifiche del sistema, descrizione di un task, descrizione di un utente tipo del sistema, sequenza dei passi necessari per compiere il task.
Per ogni passo l'esperto di psicologia solitamente, si chiede mentre esegue il task:
- L'effetto dell'azione è lo stesso dell'obiettivo dell'utente?.
- L'utente può vedere che l'azione è disponibile?.
- L'utente capirà che quella è l'azione da eseguire?.
- Dopo averla eseguita, capirà il feedback ricevuto?.
E riporta i problemi trovati su un documento.


### Heuristic evaluation

Euristica, sono le linee guida, o principio generale, o regola pratica semplice ed efficiente.

Questa tecnica serve per guidare le decisioni di progetto o per criticare decisioni già prese.

__Nielsen__ e __Molich__ hanno proposto $10$ euristiche per __scoprire problemi__ di usabilità dei sistemi interattivi.

Nella valutazione euristica il valutatore esamina il progetto per vedere se il progetto viola una o più euristiche.

1. visibilità dello stato del sistema
2. corrispondenza tra il sistema e il mondo reale
3. libertà e controllo da parte degli utenti
4. coerenza e standard
5. prevenzione degli errori
6. riconoscere piuttosto che ricordare
7. flessibilità ed efficienza d'uso
8. design minimalista ed estetico
9. aiutare gli utenti a riconoscere, diagnosticare e correggere gli
errori
10. aiuto/guida e documentazione

Per ogni euristica si procede descrivendo:
- Problema.
- Analisi.
- Soluzione.

### Model-based evalutation



### Review-based evaluation

Questa tecnica si basa su __risultati ottenuti da studi precedenti__.

È usato per supportare o rifiutare parti del design.

Un __esperto__ è richiesto per assicurarsi che il tutto sia corretto.

# Modi

content: l'insieme di informazioni che risiedono in un sistema e che hanno significato e utilità per l'utente

GID (Graphical Input Device): meccanismo per
comunicare al sistema una particolare locazione o
la scelta di un oggetto (tipicamente la posizione del
cursore)

GID button: bottone principale del GID

## Gesture (gesto)

Una gesture è una sequenza di azioni completata "automaticamente" una volta avviata.

E.g.:
- Scrivere una parola comune (autocomplete?)
- Premere il tasto invio.
- Drag and drop sul smartphone.
	- Appoggio il dito su un oggetto, tengo fermo il dito (così l'oggetto viene "agganciato")
	- Sposto il dito.
	- Stacco il dito dallo schermo.

## Modi (definizione)

I modi si manifestano nella maniera in cui un'interfaccia risponde ai gesti.

Dato un gesto, un'interfaccia è in un __modo__ se l'interpretazione di quel gesto è sempre la stessa.
E quando il gesto viene interpretato in maniera diversa, l'interfaccia si trova in un __altro modo__.

E.g. il tasto invio può essere interpretato in vari modi:
- Può essere interpretato come "andare a capo"
- Può essere interpretato come "confermare l'inserimento"
- Può essere interpretato come "seleziona l'elemento dopo aver scelto tale oggetto"

## "Luogo dell'attenzione"

Un luogo dell'attenzione è un oggetto fisico o un idea alla quale:
- Stiamo pensando __attivamente e intenzionalmente__.

Può esserci __un solo__ luogo dell'attenzione __alla volta__.

È simile al concetto di focussarsi. (Se qualcosa accade al di fuori del luogo che succede)

## Caps lock

Il tasto di blocco maiuscole __crea un modo__.

Ma solitamente gli utenti sbagliano a scrivere in maiuscolo solo dopo aver scritto un pò, __anche se__ vi sono LED verde sul tasto stesso, o altri indicatori di caps lock.

Quindi i modi __possono indurre in errore__, anche se possono comunque essere utili, aggiungendo __flessibilità__.

Ne l'esperienza ne l'inesperienza riesce a proteggere l'utente dagli errori dovuti ai modi.
- L'esperto ha semplicemente acquisito delle abitudini.

## Mode errors

Quindi gli errori causati dai modi:
- Sono errori che accadono quando un utente pensa in modo errato e/o analizza una situazione in modo sbagliato.

Come evitare questi errori:
- __Non avere__ modi.
- Assicurarsi che i modi sono marcati in modo distintivo.
- __Assicurarsi che il comando__ richiesto da __differenti modi__ non sia lo stesso, in modo tale che un comando eseguito in modo sbagliato __non porterà a difficoltà__, ovvero il comando non deve produrre alcun effetto.

Gli errori di modo provengono principalmente dagli spostamenti del luogo d'attenzione dell'utente.

Se si riesce a redesignare l'interfaccia in modo che si eliminino tutti gli spostamenti di attenzione, allora non ci saranno più errori di modo.

## Interfaccia modale

Un interfaccia è __modale rispetto a un gesto__ se:
- Lo stato corrente dell'interfaccia non è il luogo dell'attenzione dell'utente. (E.g. tipo quando stai su clash of clans e perdi la connessione esce il popup, ma il tuo luogo dell'attenzione era sulla battaglia)
__e__
- L'interfaccia risponderà al gesto con un tra n>1 possibili risposte, a seconda dello stato del sistema.
E.g. Quando un app vuole farti attivare la location, tu decidi si o no.

Le interfacce modali servono a:
- __Ottenere immediatamente l'attenzione dell'utente__ per comunicare __informazioni critiche__, __confermare azioni non reversibili__....

--
In Human-Computer Interaction (HCI),
**modes** are distinct states where the same user input (gesture, keypress, or click) results in different actions depending on the system's current condition.
-\-

A **modal interface** is one that transitions between different states or "modes". It restricts a user's interaction to a specific task or window, requiring them to complete or dismiss it before they can return to the rest of the application

**High Risk of "Mode Errors":** Users may perform an action intended for one mode while actually in another (e.g., typing a password with **Caps Lock** active, which is a common modal state).

Quindi è una cosa che cambia lo stato di un elemento in __uno specifico _modo___.

Un __quasi-modo__ è un modo ottenuto attivando e mantenendo fisicamente un controllo:
- E.g. tasto ctrl

## Interfaccia NON modale

Un interfaccia può essere modale rispetto a uno o più gesti e __non__ modale risposto a un altro o vari altri gesti.

Un'interfaccia è __non-modale__ se non è modale rispetto a qualunque possibile gesto.

## Interazione noun-verb e verb-noun

Eseguire azioni (verb) su oggetti (noun).

Sono anche chiamati object-action e action-object.

### Noun-verb

Si seleziona prima l'oggetto:
E.g. seleziono prima la gomma su photoshop, e poi cancello.
E.g. seleziono un tool da una palette di strumenti e poi lo uso.

Si seleziona l'oggetto mentre esso è nel luogo dell'attenzione.
Il luogo dell'attenzione si sposta sull'azione e la si attiva.
Interrompere l'azione non richiede un'altra azione, quindi semplice e reversibile (E.g. scelgo cancellino)

### Verb-noun

Si seleziona prima l'azione:
E.g. seleziono un testo, scelgo un nuovo font (il font è l'oggetto)

Si sposta il luogo dell'attenzione __sull'azione__ e la si seleziona.
Si sposta il luogo dell'attenzione sull'oggetto.
In caso di distrazione e spostamento imprevisto del luogo dell'attenzione, __ci saranno errori di modo__.

