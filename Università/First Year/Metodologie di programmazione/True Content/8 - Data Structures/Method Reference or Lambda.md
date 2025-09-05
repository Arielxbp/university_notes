___

# Using Method Reference
![center](https://i.imgur.com/Ufrz69r.png)

Nel codice sopra abbiamo creato una interfaccia funzionale chiamata "funzione" che prende in input una stringa e ritorna la stessa stringa ma tutta in minuscolo.

Per crearla abbiamo usato <font style="color:salmon">un riferimento a metodo</font> tramite la scrittura <font style="color:salmon">String::toLowerCase</font>.

# Using Lambda

Si può avere lo stesso effetto usando invece del riferimento a metodo, una espressione lambda per l'interfaccia funzionale:
![center](https://i.imgur.com/dVkEd9p.png)

# Sorting with Lambdas

- Si può ordinare su una collezione attraverso una interfaccia funzionale che usa una espressione lambda che implementa <font style="color:salmon">compareTo</font>.

![center](https://i.imgur.com/J86nb5g.png)

-  In questo codice l'ArrayList viene ordinato in modo inverso.

# Table with Differences between the two

![center](https://i.imgur.com/InQ0smW.png)
