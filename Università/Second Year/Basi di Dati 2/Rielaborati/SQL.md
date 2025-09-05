
## Creazione di strutture dati SQL (create)

Per effettuare la creazione di __database__, __schemi__ e __tabelle__.
```postgresql
create database nome_database;

create schema nome_schema;

create table nome_tabella ();

```

Solitamente quando si crea una tabella si includono gli attributi (colonne) della tabella.

```postgresql
create table nome_tabella(nomeAttributo1 tipoAttributo1, ...);

-- Per inserire attributi che non devono poter avere valori nulli
create table nome_tabella(nomeAttributo1 tipoAttributo1 not null);

```

Durante la creazione di una tabella si possono indicare la chiave primaria e le foreign key.

```postgresql
create table nome_tabella(nomeAttributo1 tipoAttributo1 not null,
primary key (nomeAttributo1)
foreign key (nomeAttributo1) references nome_tabella2(nomeAttributo2)
);
```

Un esempio completo è:
```postgresql
create table Incarico(docente integer not null, corso integer not null,
primary key (docente, corso),
foreign key (docente) references Docente(matricola),
foreign key (corso) references Corso(codice)
);
```

## Domini (tipi) SQL predefiniti

In SQL esistono domini predefiniti.
```postgresql
integer -- Numeri interi

varchar -- Stringhe
varchar(100) -- Stringhe lunghe massimo 100 caratteri

date -- Record (tuple) con campi per anno, mese e giorno
time -- Record (tuple) con campi per ora, minuto e secondo
timestamp -- Record (tuple) con campi per anno, mese, giorno, ora, minuto e secondo

interval -- Intervalli temporali

-- Valori booleani
bool
boolean

-- Dati non strutturati di grandi dimensioni
CLOB
BLOB
```

## Valori di default per attributi se non specificati (default)

È possibile assegnare a un attributo (colonna) un valore di default, dove durante l'inserimento o modifica di ennuple che includono quell'attributo, se non viene specificato un valore, allora prenderà di default il valore indicato alla creazione dell'attributo.

```postgresql
create table Impiegato(
nome varchar(100) not null,
cognome varchar(100) not null,
stipendio integer default 0 -- Avrà come valore di default 0
);
```

## Vincoli di dominio (check)

È possibile includere un controllo sui valori inseriti durante un'inserimento o modifica su attributi che presentano quest'opzione.

```postgresql
create table Impiegato(
nome varchar(100) not null,
cognome varchar(100) not null,
stipendio integer default 0 check (stipendio >= 0) -- Controlla se lo stipendio non è negativo
)
```

## Vincoli di chiave (unique)

È possibile indicare altre chiavi oltre alla chiave primaria

```postgresql
create table Studente(
matricola integer not null,
nome varchar(100) not null,
cognome varchar(100) not null,
nascita date,
cf varchar(16) not null,
primary key (matricola), -- Chiave primaria
unique (cf), -- Altra chiave
foreign key (cf) ref Persona(cf), -- Foreign key sul codice fiscale
)
```

## Modifica di tabelle, schemi e database

```postgresql
alter table

alter table add column
alter table drop column
alter table alter column

alter table add constraint
alter table drop constraint
```

## Cancellazione di tabelle, schemi e database

```postgresql
drop table nomeTabella

drop schema nomeSchema

drop database nomeDatabase
```

## Domini (tipi) SQL custom

È possibili definire nuovi domini.

In particolare è possibile definire:
- Domini specializzazione di altri domini.
- Domini di tipo enumerativo.
- Domini di tipo record.

```postgresql
-- Per creare domini specializzati
create domain nome_dominio as tipo_base
	default default_value
	check vincolo_di_dominio

-- E.g.
create domain voto as integer
	default 0
	check (value >= 18 and value <= 30) -- Si usa value per indicare il valore da controllare

-------------------------------------

-- Per creare domini di tipo enumerativo
create type nome_dominio as
	enum('value1', 'value2', 'value3', ..., 'valueN') -- Questi valori NON sono stringhe ma sono identificatori

-- E.g.
create type continente as
	enum('America nord', 'America sud', 'Africa', 'Europa', 'Asia', 'Oceania')

-------------------------------------

--Per creare domini di tipo record (tuple)
create type nome_dominio as(
	campo1 dominio1, ..., campoN dominioN
)

-- E.g.
create type indirizzo as(
	via varchar(200), città varchar(100)
)
```

## Modifica e cancellazione di domini custom

```postgresql
alter domain nome_dominio
alter type nome_dominio

drop domain nome_dominio
drop type nome_dominio
```

## Generazione di valori progressivi

```postgresql
create table Prenotazione(
identificativo serial not null -- Tramite l'uso di serial (sono valori di tipo intero)
)
```

## Inserimento di ennuple

```postgresql
insert into nome_tabella(attributo1, ... , attributoN)
values (valore1, ..., valoreN)

-- L'ordine con la quale si indicano i valori degli attributi è indifferente
insert into nome_tabella(attributo1, ... , attributoN)
values (valoreN, ..., valore1)
```

## Cancellazione di ennuple

```postgresql
delete from nome_tabella where condizione -- Vengono cancellate tutte le ennuple della tabella che soddisfano la condizione

-- E.g.
delete from officina where
nome = 'MotorGo' and
indirizzo = 'piazza Turing 1'

-----------------------

-- Se si omette where condizione è come se si scrivesse where true
delete from officina -- Elimina tutte le ennuple della tabella officina
```

## Modifica di ennuple

```postgresql
update nome_tabella
set attributo1 = valore_attributo1, ..., attributoN = valore_attributoN
where condizione

-- Tutte le ennuple che soddisfano la condizione avranno come valori per gli attributi i nuovi valori assegnati
```

## Interrogazioni su tabella

```postgresql
-- Se si interrogano multiple tabelle forse con nomi per attributi uguali
select nome_tabella.attributo1, nome_tabella.attributo2
from nome_tabella
where condizione

-- Se si interroga su una sola tabella
select attributo1, ..., attributoN
from nome_tabella
where condizione

-- È possibile che vi sia una richiesta di tutti gli attributi da una tabella, in quel caso usare *.
select * from nome_tabella where condizione

------------------------------------------------

-- È possibile che la richiesta sia molto specifica sui valori richiesti
select *
from nome_tabella
where attributo like 'X_%'
-- '%' indica che va bene qualunque stringa
-- '_' indica che va bene qualunque carattere

-- E.g.
select *
from Persona
where cognome like 'R_s%' -- Cognome che inizia per 'R' e ha 's' come terzo carattere (Rossi) 
```

## Distinct

La tabella restituita da una istruzione __select__ potrebbe __non__ rappresentare una relazione.
Si usa __distinct__ per indicare che non si vogliono ennuple duplicati.

```postgresql
select distinct attributo1, attributo2 -- Dato distinct non vengono restituiti ennuple uguali
from nome_tabella
where condizione
```

## Interrogazioni su più tabelle

```postgresql
select valori_attributi_che_si_vogliono
from tabella1, tabella2
where
tabella1.attributo1 = tabella2.attributo2 and
tabella2.attributo2_1 = valore2_1

-- E.g. si vogliono restituire gli indirizzi delle officine dove è stato riparato il veicolo di targa 'HK243BW'

select Officina.indirizzo
from Officina, Riparazione
where Officina.nome = Riparazione.officina
and Riparazione.veicolo = 'HK243BW'

------------------------

-- E.g. si vogliono restituire le targhe dei veicoli che sono stati riparati in almeno due diverse officine

select r1.veicolo
from Riparazione r1, Riparazione r2
where r1.veicolo = r2.veicolo
and r1.officina <> r2.officina -- Il <> significa che sono differenti, sarebbe !=
```

## Alias di tabelle

```postgresql
-- È possibile dare degli alias ai nomi delle tabelle
select o.indirizzo
from Officina as o, Riparazione as r -- Uso as
where o.nome = r.officina
and r.veicolo = 'HK243BW'

-- Ancora più ridotta
select o.indirizzo
from Officina o, Riparazione r
where o.nome = r.officina
and r.veicolo = 'HK243BW'
```

## Ordinare il risultato di una interrogazione

```postgresql
-- Il risultato di una interrogazione può essere ordinato
select *
from nome_tabella
where condizione
order by attributo asc

select *
from nome_tabella
where condizione
order by attributo desc
```

## Funzioni aggregate

Le funzioni aggregate calcolano __un singolo valore__ a partire da tutte le ennuple.

```postgresql
-- count(attributo) conta il numero di valori non NULL per l'attributo
-- E.g. si vuole restituire il numero di riparazioni del veicolo 'HK243BW'
select count(*) -- Conta il numero di ennuple della tabella restituita
from Riparazione as r
where r.veicolo = 'HK243BW'

-- E.g. si vuole restituire il numero di officine distinte che hanno riparato il veicolo 'HK243BW'
select count(distinct officina) -- Conta il numero di ennuple distinte della tabella restituita contenente nomi di officine
from Riparazione as r
where r.veicolo = 'HK243BW'

----------------

-- Altre funzioni aggregate
sum(attributo) -- Somma su domini numeri o tempo
avg(attributo) -- Valore medio su domini numeri o tempo
min(attributo) -- Valore minimo su domini ordinati
max(attributo) -- Valore massimo su domini ordinati
```

__Non__ si può avere come risultato di un interrogazione attributi e funzioni aggregate:
```postgresql
select nome, avg(stipendio)
from Persona
```
Restituirebbe ennuple composte dai nomi delle persone e lo stipendio medio di chi?

Quindi i risultati devono essere __omogenei__, ovvero se contiene funzioni aggregate allora non può contenere attributi e viceversa.

Esiste un'eccezione a questa regola quando si usa il __group by__/

## Raggruppamenti (group by)

Si possono raggruppare le ennuple prima di effettuare le funzioni aggregate su questi gruppi.

```postgresql
-- Si vogliono restituire i nomi delle persone con figlio e con stipendio >= 45, insieme al numero dei loro figli.

select p.id as pid, p.nome as genitore, count(f.nome) as nFigli
from Persona p, GenitoreFiglio gf, Persona f
where p.id = gf.gen and
gf.figlio = f.id and
p.stipendio >= 45
group by g.id, g.nome
having count(f.nome) >= 2 -- I genitori con minimo due figli
```

L'ordine di esecuzione della query è:
1) Si esegue l'interrogazione __select__ con where __condizione__.
2) Si partizionano le ennuple risultanti mettendo nella stessa partizione quelle che coincidono nei valori di tutti gli attributi definiti dopo il group by.
3) Per ogni partizione si calcolano indipendentemente i valori delle funzioni aggregate.
4) Si restituisce __una__ ennupla __per ogni partizione__, e questa ennupla contiene gli attributi definiti dopo il group by e i valori delle funzioni aggregate per la singola partizione.
5) Inoltre se viene usata la clausola __having__ allora si includono solamente le ennuple per le partizioni che soddisfano la condizione having.

## Unione

```postgresql
-- Restituisce l'unione delle ennuple restituite da query1 e query2 (di default elimina i duplicati)
query1
union
query2

-- Restituisce l'unione delle ennuple restituite da query1 e query2 mantenendo i duplicati
query1
union all
query2

-- E.g. 
select padre as genitore, figlio
from paternità
union
select madre as genitore, figlio
from maternità
```

## Differenza

```postgresql
-- Restituisce le ennuple di query1 che non sono in query2
query1
minus
query2

-- E.g.
select nome
from Impiegato
minus
select cognome
from Impiegato
```

## Intersezione

```postgresql
-- Restituisce le ennuple comuni a query1 e query2 (si usa il join se serve l'efficienza)
query1
intersect
query2

-- E.g
select nome
from Impiegato
intersect
select cognome
from Impiegato

-- equivale a scrivere
select nome
from Impiegato i, Impiegato j
where i.nome = j.cognome
```