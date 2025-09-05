___

# Domande vero/falso

## Numero 1
Falso

## Numero 2
Vero

## Numero 3
Falso

## Numero 4
Vero

## Numero 5
Vero

## Numero 6
Falso

# Esercizio 1
GET /usr/web/appello1.html HTTP/1.1
Host: www.esamidireti.it
Connection: close
Content-type: text/plain, text/html, image/png
Last/modified: almeno 24 fa

I passi sono richiesta DNS del hostname www.esamidireti.it
quindi la richiesta passa dal server DNS locale, cache se no allora Server dns TLD, poi autorità che risponde con un ip

Il CNAME it è un dominio, non è un alias
se è CNAME, si aspetta che il RR è tipo < nomeserversemplice, nomeserversupercomplicato >

Se tempo di trasmissione == tempo di propagazione, allora __non__ si può dire che un host A ha già ricevuto almeno un bit dall'host B

Esiste un timer di base anche se non specificato per l'esercizio dei Ack
Differenziare tra Ack cumulativo (entro il timer arriva pacchetto successivo) e Ack posticipato ()

Nel grafico si parte da 1

I slow start finisco al pallino prima
quindi non a 4 ma a 3

Se Fast Recovery non è esponenziale allora vuol dire che è arrivato subito un ack nuovo quindi subito diventa Congestion Avoidance
quindi l'unita di tempo di fast recovery sarà solo 38
