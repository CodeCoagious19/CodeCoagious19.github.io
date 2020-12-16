---
layout: page
title: Corso Python - 17
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 18
---

## Python - List Comprehension

*List Comprehension* offre una sintassi più breve quando si desidera creare un nuovo elenco basato sui valori di un elenco esistente.

[w3schools - Python - List Comprehension](https://www.w3schools.com/python/python_lists_comprehension.asp)

E' una sorta di **RegEx** utilizzata per il tipo **List**.
Sintassi.

```py
newlist = [expression for item in iterable if condition == True]
```

Nell'esempio che segue costruisco una lista non utilizzando *List Comprehension*:

```py
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = []

#La nuova lista conterrà soltanto elementi che contengono il carattere "a"
for x in fruits:
  if "a" in x:
    newlist.append(x)

print(newlist) #["apple", "banana", "mango"]
```

Il solito esempio utilizzando *List Comprehension*:

```py
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]

#List Comprehension
newlist = [x for x in fruits if "a" in x]

print(newlist)
```

E' una sintassi molto vicina alla sintassi del linguaggio matematico.. Può essere infatti tradotto nel seguente modo: << Cerca le "x" all'interno della lista "fruits" tali che il carattere "a" è contenuto in "x">>

Nel seguente esempio elenco i numeri dispari da 0 a 100 con una sola espressione *List Comprehension*:

```py
#Cerca le x da 0 a 100 tali che il risultato della divisione intera tra x e 2 moltiplicato successivamente per 2 sia diverso da x
#es: 3/2 = 1 >> 1*2 = 2 >> 3!=2 >> print
#es: 4/2 = 2 >> 2*2 = 4 >> 4=4 
print([x for x in range(0, 100) if x // 2 * 2 != x])
```

