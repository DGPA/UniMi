---
title: Programmazione Teoria
numbersections: true
geometry:
- top=12.7mm
- left=12.7mm
- right=12.7mm
- bottom=12.7mm
---

# Tipi base in Go
- bool
- string
- int   int8    int16   int32   int64
- uint  uint8   uint16  uint32  uint64  *uintptr*
- byte
- rune
- float32   float64
- complex64 complex128

int e uint sono "implementation dependent" (occupano 32 0 64 bit in base all'architettura della macchina in cui si esegue il codice)

# Variabili

Le variabili sono un contenitore, identificati da un nome univoco, di un qualsiasi valore

## La vita di una variabile

1. Dichiarazione:
    - Keyword: var
    - Identificatore: nome della variabile
    - tipo: tipo della variabile
1. Definizione (inizializzazione o allocazione)
1. Utilizzo
1. Rilascio

## Scope

Parte del codice in cui una variabile è accessibile.

## Dichiarazione e definizione breve

```go
numeroIntero := 22              //tipo int
numeroFloat := 20.19            //tipo float64
carattere := 'a'                //tipo int32
stringa := "Hello World!"       //tipo string
```

## Costanti

È buona norma scrivere le constanti in maiuscolo.
```go
const NOMECOSTANTE tipo = valore
```

# Operatori in Go

## Operatori binari

| Binari | Descrizione                       |
|--------|-----------------------------------|
| *      | Moltiplicazione                   |
| /      | Divisione                         |
| %      | Calcolo del resto della divisione |
| \|     | OR binario                        |
| ^      | XOR binario                       |
| &      | AND binario                       |
| &^     | AND NOT binario                   |
| +      | Somma                             |
| -      | Sottrazione                       |
| <<     | Shift a sinistra                  |
| >>     | Shift a destra                    |
| ==     | Verifica ugguaglianza             |
| !=     | Verifica diversità                |
| <      | Minore                            |
| <=     | Minore o uguale                   |
| >      | Maggiore                          |
| >=     | Maggiore o uguale                 |
| &&     | AND logico                        |
| \|\|   | OR logico                         |

## Operatori unari

| Unari | Descrizione           |
|-------|-----------------------|
| ++    | Incrementa di 1       |
| --    | Sottrae di 1          |
| +     | Più unario            |
| -     | Meno unario           |
| !     | Not                   |
| ^     | Complemento a 1       |
| *     | Valore dell'indirizzo |
| &     | Indirizzo             |
| <-    | Ricevitore            |

# Errori

- **Lessicale**: uso di parole chiave del linguaggio non esistenti o scritte in maniera errata
- **Sintattico**: uso di parole chiave del linguaggio scritte correttamente ma utilizzate in maniera errata
- **Semantico** (*o logico*): fornisce un output incoerente o si comporta in un modo inaspettato
- **Estetico** (*o pragmatico*): scelta di andare a capo errata, indentazione errata (distribuzione del codice) e scelta dei nomi degli identificatori poco chiara

# If

```go
if condizione {
    //se la condizione è vera esegue queste istruzioni
} else {
    //altrimenti se la condizione è falsa esegue queste istruzioni
}
```

# For

Per sapere la lunghezza di: stringhe, array, slice e mappe si può usare la funzione `len()`

## Unario

```go
for condizione {
    //se la condizione è vera esegue queste istruzioni
}
```

## Ternaria

```go
for istruzione iniziale; condizione; aggiornamento {
    //se la condizione è vera esegue queste istruzioni
}
```

## Zeraria

```go
for {
    //se la condizione è vera esegue queste istruzioni
}
```

Attenzione! Creare una condizione nella quale sia possibile usare `break` per uscire dal ciclo altrimenti il ciclo sarà infinito.

`continue` invece permette di passare alla successiva iterazione.

## Range

Si usa per scorrere su tutta la lunghezza delle stringhe, array, slice e mappe

```go
var i int
var v tipo
for i, v := range variabile {
    //sequenza di istruzioni
}
```

# Sottoprogramma

Utile per rendere il codice modulare e per aumetare la leggibilità 
```go
func nomeSottoprogramma(parametri formali e tipo dei parametri formali) tipo del valore restituito {
    //sequenza di istruzioni
}
```

Attenzione! I parametri sono passati per copia.

## Utilizzo

```go
nomeSottoprogramma(parametri effettivi)
```

## Scope

**camelCase**: (scrivere parole attaccate con ogni iniziale maiuscola, tranne la prima) rende il sottoprogramma privato (accessibile solo nello stesso file)

**PascalCase**: (scrivere parole attaccate con ogni iniziale maiuscola) rende il sottoprogramma Pubblico (accessibile in tutti i file in cui si sia importato il package)

# Selezione multi-aria: Switch - case

```go
switch espressione testa {
case espressione1a, espressione1b: 
    //sequenza di istruzioni se il case è valido
case espressione2:
    //sequenza di istruzioni se il case è valido
default:
    //sequenza di istruzioni se i case sopra non sono validi
}
```
Quando si entra in un case poi si esce dal costrutto. Il `default` è opzionale

# Packages Utili

## fmt

Per le Print è possibile andare a capo con `\n`

### Print

Stampa il contenuto nelle parentesi.
```go
fmt.Print()
```

### Println

Stampa il contenuto nelle parentesi poi va a capo
```go
fmt.Println()
```

### Printf

Stampa il contenuto nelle parentesi, si possono utilizzare diversi verbi
```go
fmt.Printf()
```

| Principali verbi per Integer | Descrizione       |
|------------------------------|-------------------|
| %d                           | base 10           |
| %c                           | carattere unicode |
| %b                           | base 2            |
| %x                           | base 16           |
| %o                           | base 8            |

| Principali verbi per String e Slice | Descrizione     |
|-------------------------------------|-----------------|
| %s                                  | stringa o slice |

| Principali verbi per Float | Descrizione     |
|----------------------------|-----------------|
| %f                         | numeri decimali |

| Principali verbi per Bool | Descrizione  |
|---------------------------|--------------|
| %t                        | true o false |

# Ascii

128 caratteri da 0 a 127 rasppresentabili con 1 byte.

## Tipo byte

Alias uint8

# Unicode

I primi 128 "grafemi" sono gli stessi dell ASCII e sono necessari fino a 4 byte.

## Rune

Alias di int32

# Stringhe

Sequenza di `byte` ovvero un array di byte

# Array

sequenza di variabili dello stesso tipo di dimensione statica

`var nomeArray [lunghezza]tipo`

```go
var n [4]int = [4]int{1, 2, 3, 4}
n = [4]int{5, 6, 7, 8}
n2 := [4]int{9, 10, 11, 12}
```

# Puntatori

Utili per locazione, indirizzo e contenuto

`&` referenziazzione (l'indirizzo).

`*` dereferenziazzione o indirezione (valore)

`var nomePuntatore *tipo`

```go
package main

import "fmt"

func main(){
	var b int = 20
	var a *int = &b
	fmt.Println("L'indirizzo di 'b' è ", a)
	fmt.Println("Il valore di 'b' è ", *a)
	sommo2(a) //Modifico 'a'
	fmt.Println("Il valore di 'b' dopo la modifica ad 'a' è ", b)
}

/*
Sto passando per copia il puntatore 'a', ma dato che 'a' ha come indirizzo l'indirizzo di 'b',
è come se stessi modificando 'b'
*/
func sommo2(n *int){
	*n = *n + 2
}
```

# Slice

Sequenza puntatori di variabili dello stesso tipo di dimensione dinamica.

`var nomeSlice []tipo`

Per inizializzarla si usa la funzione `make()`

`nomeSlice = make([]tipo, lunghezza, capacità)`

Per aumentare la dimensione di 1 e aggiungere un valore si usa la funzione `append()`

Per sapere la lunghezza della capacità degli slice si può usare la funzione `cap()`
```go
var s []int
s = make([]int, 4, 20)
s = append(s, 2)
```

## Subslice

In Go si possono creare delle subslice (parti della slice). Per creare delle subslice si usa il nome della slice e la posizione iniziale inclusa e la posizione finale esclusa separate da `:` e comprese da `[]`.

`nomeSlice[inizioIncluso:fineEscluso]`

Se si omette la posizione iniziale essa coinciderà con la posizione iniziale della slice, mentre se si omette la posizione finale essa coinciderà con la posizione finale della slice.
```go
var slice []int = []int{1, 2, 3, 4, 5}

var subSlice1 []int = [1:3]
var subSlice2 []int = [1:]
var subSlice3 []int = [:3]
var subSlice4 []int = [:]
```