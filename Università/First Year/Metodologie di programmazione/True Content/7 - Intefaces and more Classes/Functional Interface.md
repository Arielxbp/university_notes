___

- [[Later Introduced things|In Java 8]] è disponibile una nuova annotazione: <font style="color:salmon">@FunctionalInterface</font>.

- L'annotazione <font style="color:salmon">garantisce</font> che l'interfaccia sia dotata esattamente di un solo metodo astratto. (può avere comunque altri metodi <font style="color:salmon">non astratti</font>)

# Built-in Functional Interfaces

- <font style="color:salmon">Predicate</font>\<T>: funzione booleana a un solo argomento di tipo T generico.

- <font style="color:salmon">Function</font>\<T,R>: funzione a un argomento di tipo T e un tipo di ritorno R entrambi generici.

- <font style="color:salmon">Supplier</font>\<T>: funzione senza argomenti in input e un tipo di ritorno T generico.

- <font style="color:salmon">Consumer</font>\<T>: funzione con un argomento di tipo generico T e nessun tipo di ritorno.



# Interfacce Funzionali Notevoli (tf?)
___

- posso riferirmi a un metodo purchè la signatura di quel metodo sia compatibile con la signatura dell'unico metodo astratto dell'interfaccia funzionale
????????????????????????
