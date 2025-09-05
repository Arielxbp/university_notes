#java 
___

Da Java 8 esiste la possibilità di usare le espressioni Lambda:
```java
() -> {System.out.println("buh");}
```
Vengono usate nelle [[Interface (Interfacce)#Functional Interface(Interfaccia funzionale)|interfacce funzionali]].

La sintassi è:
```java
(tipo1 nome_parametro1, ...) -> {codice della funzione}
```
Il tipo dei parametri in input è opzionale.
Anche le parentesi tonde sono opzionali **se** si usa un solo parametro.
Anche le parentesi graffe sono opzionali se il codice è su singola riga.

- L'uso di <font style="color:Indianred">espressioni Lambda</font> è preferibile quando il codice si riesce a scrivere su una singola riga.

