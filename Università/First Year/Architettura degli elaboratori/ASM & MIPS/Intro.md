<font style="color:salmon">OUTLINE WIP</font>
MIPS
	//
Tipi di registri
	Registri per gli argomenti
	Registri per i valori di ritorno
	Registri temporanei
	Registri "salvati"
Tipi di istruzioni di MIPS
	Istruzioni matematiche
		Somma / Somma immediata
		Sottrazione
		Moltiplicazione // manca
		Divisione // manca
		Resto // manca
	Istruzioni di trasferimento di dati
		Lettura immediata di una Word (parola)
		Lettura di una Word (parola)
		Copia di una Word (parola) da un registro a un altro
		Memorizzazione di una Word (parola)




# MIPS
___
- MIPS è di tipo RISC, ovvero un architettura con un set di istruzioni molto più semplici e ridotti rispetto all'architettura CISC.

- MIPS ha <font style="color:salmon">32</font> registri.

  Gli operandi devono essere contenuti nei registri per potere eseguire operazioni.
  
  Il registro <font style="color:salmon">$zero</font> contiene sempre il valore $0$ (zero).
  Il registro<font style="color:salmon">$at</font> viene riservato all'assemblatore per la gestione di costanti molto lunghe.

- Il MIPS usa l'indirizzamento al byte, <font style="color:salmon">perciò due parole consecutive hanno indirizzi in memoria a una distanza di 4</font>.

- La <font style="color:salmon">Word</font> di default del MIPS è di 32 bit.
- Una memoria contiene $2^{30}$ <font style="color:salmon">Word</font> (parole)
  
  Quindi se si sta all'indirizzo $x$ e si vuole leggere la Word successiva, si deve incrementare l'indirizzo a $x+4$ perché una Word sono 4 [[Representation of data in machines#Bits, Nibbles e bytes|Byte]] ossia 32 [[Representation of data in machines#Bits, Nibbles e bytes|Bit]].

# Tipi di registri
___
Solitamente si usano $4$ tipi di registri:
- argomenti
- valori di ritorno
- temporanei
- salvati

![](https://i.imgur.com/kVncq4O.png)

Esistono anche alcuni registri "speciali" come:
- registro zero
- registri riservati (per esempio $at)

## Registri per gli argomenti

- Questi servono <font style="color:salmon">per passare valori ALLE funzioni</font>.

- Sono $4$:
```Verilog
$a0, $a1, $a2, $a3
// Significato in pseudocodice: func($a0, $a1, $a2, $a3):
```

## Registri per i valori di ritorno

- Questi servono <font style="color:salmon">per restituire valori DALLE funzioni</font>.

- Sono $2$:
```Verilog
$v0, $v1
// Significato in pseudocodice: return $v0, $v1
```

## Registri temporanei

- Questi servono <font style="color:salmon">per storare valori temporaneamente(?)</font>.

- Sono $10$:
```Verilog
$t0, $t1, $t2, ..., $t8, $t9
```

## Registri "salvati"

- Questi servono <font style="color:salmon">per boh(?)</font>.

- Sono $8$:
```Verilog
$s0, $s1, $s2, ..., $s6, $s7
```

# Tipi di istruzioni in MIPS
___
- Aritmetiche
- Trasferimento di dati
- Logiche
- Salti condizionati
- Salti incondizionati

## Istruzioni matematiche
___
- Lo stesso registro può essere usato <font style="color:salmon">sia come operando</font>, <font style="color:salmon">sia come registro per salvare il risultato</font>.
- L'ultimo operando può essere<font style="color:salmon"> un registro oppure una costante</font>.
- Il risultato <font style="color:salmon">deve stare sempre a sinistra</font>.

### Somma / Somma immediata

- La somma <font style="color:salmon">add</font> viene eseguita usando $3$ registri:
  $2$ registri dove sono presenti i numeri da sommare.
  $1$ registro dove salvare il risultato della somma.
```Verilog (MIPS)
add $s1, $s2, $s3 // Significato: $s1 = $s2 + $s3
```

- La somma <font style="color:salmon">addi</font> viene eseguita usando 2 registri:
  $1$ registro dove è presente uno dei due numeri da sommare.
  $1$ registro dove salvare il risultato della somma.
```Verilog
addi $s1, $s2, 20 // Significato: $s1 = $s2 + 20
```

### Sottrazione

- La sottrazione <font style="color:salmon">sub</font> viene eseguita usando $3$ registri:
  $2$ registri dove sono presenti i numeri da usare.
  $1$ registro dove salvare il risultato della sottrazione.
```Verilog
sub $s1, $s2, $s3 // Significato: $s1 = $s2 - $s3
```

### Moltiplicazione

- wip

### Divisione

- wip
### Resto (modulo)

- wip

## Istruzioni di trasferimento di dati
___

### Lettura immediata di una Word (parola)

- Per la lettura immediata di una Word si usa <font style="color:salmon">li</font>:
  Serve per "caricare" una <font style="color:salmon">costante</font> nel registro.
```Verilog
li $s1, 7 // Significato: $s1 = 7
```
### Lettura di una Word (parola)

- Per la lettura di una Word si usa <font style="color:salmon">lw</font>:
  Serve per il trasferimento di una Word dalla memoria al registro.
  (Copia un valore dalla memoria e la incolla nel registro)
```Verilog
lw $s1, 20($s2) // Significato: $s1 = Memoria[$s2 + 20]
```

### Copia di una Word (parola) da un registro a un altro

- Per copiare una Word da un registro a un altro si usa <font style="color:salmon">move</font>:
  Serve per copiare il valore di una Word da un registro e incollarlo in un altro registro.
```Verilog
move $s1, $s2 // Significato: $s1 = $s2
```
 ![center](https://i.imgur.com/cFR7bII.png)
### Memorizzazione di una Word (parola)

- Per la memorizzazione di una Word si usa <font style="color:salmon">sw</font>:
  Serve per il trasferimento di una Word dal registro alla memoria.
  
```Verilog
sw $s1, 20($s2) // Significato: Memoria[$s2 + 20] = $s1
```

## Istruzioni Logiche
___

### And / And immediato

- Per fare l'operazione logica AND si usa <font style="color:salmon">and</font>:
  Esegue l'AND <font style="color:salmon">bit a bit</font>.
```Verilog
and $s1, $s2, $s3 // Significato: $s1 = $s2 & $s3
```

- Per fare l'operazione logica AND immediato si usa <font style="color:salmon">andi</font>:
  Esegue l'AND <font style="color:salmon">bit a bit</font> tra un operando in registro e una costante.
```Verilog
andi $s1, $s2, 23 // Significato: $s1 = $s2 & 10111
```



\<font style="color:salmon"></font>
\<font style="color:salmon">$</font>


