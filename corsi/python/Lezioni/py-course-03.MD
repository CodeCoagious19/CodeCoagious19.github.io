---
layout: page
title: Corso Python - 04
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 4
---

## Costrutto condizionale `if...else`

Le istruzioni condizionali vengono utilizzate per eseguire un blocco di codice solo nel caso in cui una condizione risulti *true* o *false*

Sintassi costrutto `if` esteso:

```py
if condition1:
    #code 01
    #..
elif condition2:
    #code 02
    #..
else:
    #code 03
    #..
```

Esempio:

```py
print("Inserisci due numeri..)

primoValore = input()
secondoValore = input()

if a > b:
    print("Il primo valore inserito, " + primoValore + " è maggiore del secondo valore inserito, " + secondoValore)
elif b > a:
    print("Il secondo valore inserito, " + secondoValore + " è maggiore del primo valore inserito, " + primoValore)
else:
    print("i due valori inseriti sono uguali")
```

Notare che per il costrutto `if` in python, la `condition` è priva di parentesi tonde `( )` comuni invece a molti altri linguaggi di programmazione; l'operatore `:` è usato come terminatore della `condition` e l'indentazione è necessaria per racchiudere la porzione di codice condizionato da `if`.

## Costrutto iterativo `for`

Un ciclo `for` viene utilizzato per iterare su una sequenza (che può essere una lista, una tupla, un dizionario, un insieme o una stringa).

È meno simile alla *keyword* `for` in altri linguaggi di programmazione e funziona più come un metodo iteratore che si trova in altri linguaggi di programmazione orientati agli oggetti.

[w3schools - Python For Loops](https://www.w3schools.com/python/python_for_loops.asp)

Sintassi:

```py
#Sintassi 1:
for target_list in expression_list:
    #code
```

Esempio:

```py
for numero in [1, 2, 3, 4, 5]:
    print(numero*numero)

# 1
# 4
# 9
# 16
# 25

for frutto in ["banana", "mela", "pera"]:
    print(frutto)

# banana
# mela
# pera
```

## Indentazione Python
Il linguaggio python, a differenza di altri linguaggi come C/C++, Javascript .. Non utilizza delimitatori di blocco codice come `{ }` ma si affida alla semplice **indentazione**. Rende quindi indispensabile l'uso di un buon editor di testo per evitare problemi di sintassi o semantica (in alcuni casi nemmeno troppo rari). Non utilizza neanche un terminatore di statement come il classico `;` ma si affida al carattere `a capo`. L'interprete python comunque è in grado di rilevare errori sintattici di indentazione e segnalarlo.

## range() Function

Per iterare un insieme di codice un numero di volte specificato, possiamo usare la funzione `range ()`.
La funzione  `range (number)` restituisce una sequenza di numeri, a partire da 0 per impostazione predefinita, incrementa di 1 (per impostazione predefinita) e termina con un numero specificato tramite il parametro *number*. In realtà termina con il numero `number - 1`.<br>
La funzione `range ()` può accettare 1, 2 o 3 parametri:

- `range(number)`: **un parametro**, genera una lista numerica incrementale nel range `0 - number-1` 
- `range(numberStart, numberEnd)`: **due parametri**, genera una lista numerica incrementale nel range `numberStart - numberEnd-1` 
- `range(numberStart, numberEnd, step)`: **tre parametri**, genera una lista numerica con incremento pari a `step` nel range *massimo* `numberStart - numberEnd-1` 

[w3schools - The range() Function](https://www.w3schools.com/python/python_for_loops.asp)

```py
range(5)       #[0, 1, 2, 3, 4]
range(1, 5)    #[1, 2, 3, 4]
range(1, 5, 2) #[1, 3]
```

```py
for target_list in range(number):
    #code
```

```py
# range(number) costruisce una lista da 0 a number-1
for numero in range(5):
    print(numero*numero)

# 0
# 1
# 4
# 9
# 16

for numero in range(1, 5, 2):
    print(numero)

# 1
# 3
```

Nel seguente esempio specifico alla funzione `print()` di non utilizzare il terminatore di default `a capo` rendendo nullo l'attributo `end` 

```py
print(end="")
```

Esempio:

```py
for numero in range(5):
    print(str(numero) + ":", end="")
    print(numero*numero)

# 0:0
# 1:1
# 2:4
# 3:9
# 4:16
```

---

<div class="next-prev">
    <a href="./py-course-02.html" id="prev-link"> previus </a> 
    <a href="./py-course-04.html" id="next-link"> next </a>
</div>