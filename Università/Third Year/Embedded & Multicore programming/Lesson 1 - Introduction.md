___

```c
cores=8
n=24
values_for_each=n/cores
first_in_range_for_core_x=values_for_each*core_x_number
last_in_range_for_core_x=values_for_each*(core_x_number+1)
```

```c
if (is_master_core) {
	sum = local_sum;
	for each core other than myself {
		# receive value from other cores
		sum += value;
	}
} else {
	# send local_sum to master core
}
```

Ulteriore ottimizzazione:
- Assegnare multipli master core attraverso un metodo ad albero.
In questo modo da un __tempo lineare__ si passa a un __tempo logaritmico__.

La possibilità di un compilatore di rimpiazzare __codice seriale__ con __codice parallelizzato__ è complicato:
- Se vi è una funzione con __stato__, ovvero che dati due input, restituisce diversi output (in quanto magari si basa sull'iterazione precedente), quindi non è corretto chiamare tali funzioni più volte, aspettandosi output uguali (cioè senza stato).

Il parallelismo quindi è possibile da implementare usando:
- __Task parallelism__, dove si dividono vari compiti tra i core.
- __Data parallelism__, dove si dividono i dati tra i vari core.

Se ogni core ha la possibilità di eseguire task in modo __indipendente__, allora il codice da scrivere sarà simile al codice da scrivere in modo __seriale__.

In generale, multipli core necessariamente devono __coordinarsi__ in qualche modo, per diverse ragioni:
- __Comunicazione__,
- __Bilanciamento dei lavori__,
- __Sincronizzazione__,

