___


# Interrupt
- Interrompono la normale esecuzione del processore
- come conseguenza all'interrupt viene eseguito del software del SO
- possono essere sincrone o asincrone, ovvero immediate oppure sollevate dopo
- le interrupt dei programmi sono le uniche sincrone, in quanto sono conseguenza immediata di una istruzione.
- Una system call (syscall) è un interrupt che viene fatto intenzionalmente, sono anche chiamata eccezioni
- Ogni interrupt blocca il programma che l'ha generato e viene gestito l'interrupt da una funzione chiamata interrupt handler e alla fine del handler, se possibile viene fatto continuare l'esecuzione dalla istruzione successiva al interrupt

# Interleaving
- Esecuzione alternata di processi multipli

# SO
- È un insieme di programmi, eseguito dal processore come ogni altro programma, ogni spesso lascia andare altri processi in esecuzione per poi riprendere il controllo tramite interrupt
- Gestisce le risorse hardware, offre servizi agli utenti, è un interfaccia tra le applicazioni e l'hardware
- Deve permettere: [[#Interleaving]], assegnare risorse, proteggere le risorse date a un processo da altri processi che ne vogliono l'accesso, scambio di informazioni tra processi, sincronizzazione tra processi

# Kernel

- È la parte di SO che si trova sempre in ram
- Due tipi di Kernel: (1) monolitico, (2) microkernel
- monolitico: tutto il kernel in ram dal boot allo spegnimento
- microkernel: minima parte del kernel in ram, resto caricato quando serve
- ### Linux è monolitico ma presenta i moduli
# Modi di esecuzione del SO
- (1) Kernel separato, quindi SO eseguito come un'entità separata con privilegi più alti, e quindi ha una zona di ram dedicata sia per i dati che per il codice sorgente e lo stack
- (2) SO eseguito all'interno di un processo utente
- (3) SO eseguito come un insieme di processi di sistema con privilegi più alti, e partecipano alla competizione con i processi utente per il processore
- ### Linux usa una via di mezzo tra (2) e (3)
# Multiprogramming
- Esecuzione di multipli processi allo stesso tempo

# PCB (Process Control Block)
- Contiene gli elementi di un processo (stato del processo(blocked, ready,...), id, puntatori alla memoria, info generali)
- È creato e gestito dal SO
- Permette al SO di gestire più processi contemporaneamente
- Contiene info per bloccare e far riprendere un processo senza problemi
- Contiene flag, segnali, messaggi per le comunicazioni tra processi

# Dispatcher
- È un piccolo programma
- Il suo ruolo è di sospendere un processo per far eseguire altri processi
- Fa parte del SO
- È sempre in memoria (quindi nel kernel)
- Vedere [[#Scheduling/Scheduler|Short Term Scheduling]]

# Stato Blocked/Suspended
- Blocked quando un processo viene bloccato in attesa di un evento (tipo lettura file)
- Suspended quando un processo bloccato viene mandato dalla ram al disco per liberare spazio per altri processi nella ram

# Tabella di controllo del SO
- Esiste la tabella dei processi, dei file, dei device(I/O), della memoria
- Quella di memoria contiene info sull'allocazione della memoria da parte dei processi, attributi per la protezione di zone di ram, info per la gestione della memoria virtuale
- Quella dei device gestisce i dispositivi e i canali di I/O, quindi i loro stati, la disponibilità e la posizione in memoria del sorgente del trasferimento I/O
- Quella dei file contiene informazioni sul dove e sul come dei file
- Quella dei processi è una tabella che contiene i [[#PCB (Process Control Block)|PCB]] dei processi

# PID
- duh

# PSW (Program status word)
- È lo stato del processore
- È dato dai contenuti dei registri del processore

# Modalità di esecuzione del processore
- Modalità utente e modalità kernel
- Modalità kernel per gestione dei processi, della ram e del I/O, per gestire gli interrupt, le eccezioni
- Un processo utente inizia sempre in modalità utente, e se ha bisogno di passare a kernel mode per eseguire syscalls o altro, viene usato un interrupt che porta il processo a modalità kernel e dopo aver finito di fare le cose nella modalità kernel, il interruput handler finisce riportando il processo da kernel a user mode

# Thread
- sono una sottounità di processo, dato che un processo può avere più flussi di esecuzione, questi flussi sono chiamati thread
- diversi thread di uno stesso processo condividono tutte le risorse tranne lo stack delle chiamate e il processore
- vengono usati in quanto più semplici da gestire e usare, e più efficienti
- Il SO non vede i thread, è grazie a un thread library che simula i thread come processi per il SO
- I kernel level thread sono visibili dal SO in quanto non hanno bisogno di una libreria, quindi possono essere gestiti meglio
- i user level thread non sono visibili dal SO e quindi non posso essere gestiti in modo parallelo
- ### In Linux ogni processo è un thread chiamato Lightweight process

# Fork() (UNIX)
- Dato il numero n di processi che fanno fork(), alla fine il numero di processi sarà 2\^n
- tipo se 3 processi pid_1 = fork(); pid_2 = fork(); pid_3 = fork(); allora alla fine i processi nel sistema saranno 8

# Scheduling/Scheduler
- parte del SO che serve ad allocare il tempo di esecuzione per ciascun processo
- 4 scheduler:
- (1) Long term, che decide in quale ordine vengono ammessi i processi
- (2) Medium term, che decide dove inserire il processo, ram o secondaria
- (3) short term, che decide chi far eseguire nel processore
- (4) I/O scheduling, che decide a quale processo dare il dispositivo di I/O tra i vari processi che l'hanno chiesto
- Il [[#Dispatcher]] fa parte del Short Term scheduling
- Il Short Term decide in due modi:
- (1)Preemptive, dove il SO può interrompere il processo in esecuzione solitamente dopo un tot di tempo del clock (quanto di tempo), in questo caso il processo interrotto torna nella coda ready
- (2)Non-preemptive, dove un processo in esecuzione continua fino alla fine se non arriva una richiesta bloccante come una richiesta di I/O
- Ci sono vari algoritmi di scelta dei processi:
- (FCFS): è non preemptive, favorisce quelli che usano molto la CPU(CPU-bound)
- (ROUND ROBIN): è preemptive attraverso un clock, un interrupt viene generato periodicamente, favorisce i CPU-bound, cioè quelli che usano molto la cpu
- (ROUND ROBIN VIRTUALE): come round robin ma quelli I/O-bound invece che bloccarsi e mandati nella coda blocked vengono mandati in una coda con priorità
- (Shortest Process Next): SPN, no preemption, possibile starvation per processi lunghi
- (Shortest remaining time): SRT, come SPN ma preemptive attraverso un predict del processo con il tempo più breve per completamento
- (Highest response ratio next): massimizza il tempo di risposta, quindi buono per utente che nota il cambiamento subito
- ### In UNIX si usa round robin con code
- ### In Linux si usano delle runqueues e waitqueues, ogni runqueue ha una priorità e il short term pesca da queste runqueues
