---
layout: page
title: Corso Python - 06
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 7
---

## Copia di Liste

Abbiamo visto nel paragrafo precedente che per la copia di liste è sufficiente utilizzare l'operatore `[:]` ma che non vale per liste annidate. In questa lezione approfondiremo l'operazione di copia di elementi.

Copia semplice, valida per liste non annidate:
```py
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]
myList2 = myList[:]

print(myList)  #['banana', 'kiwi', 'mela', 'mandarino', 'cachi']
print(myList2) #['banana', 'kiwi', 'mela', 'mandarino', 'cachi']
```

Cosa succede se eseguo la copia tramite il semplice assegnamento?
```py
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]
myList2 = myList

print(myList)  #['banana', 'kiwi', 'mela', 'mandarino', 'cachi']
print(myList2) #['banana', 'kiwi', 'mela', 'mandarino', 'cachi']
```

Sfruttando quindi l'operatore di assegnamento `=` non ottengo una copia dei valori ma una copia dei riferimenti. In pratica in questo modo *myList* e *myList2* condividono gli stessi dati. Se modifico uno modifico anche l'altro


```py
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]
myList2 = myList

#Togliendo l'elemento da "myList" lo tolgo anche da "myList2" perchè condividono gli stessi elementi
myList.remove("banana")

print(myList)  #['kiwi', 'mela', 'mandarino', 'cachi']
# !!!
print(myList2) #['kiwi', 'mela', 'mandarino', 'cachi']
```

Ciò non accade con la copia poichè diventano due liste indipendenti:

```py
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]
myList2 = myList[:]

myList.remove("banana")

print(myList)  #['kiwi', 'mela', 'mandarino', 'cachi']
print(myList2) #['banana', 'kiwi', 'mela', 'mandarino', 'cachi']
```

**Attenzione!** Per liste più complicate come liste annidate l'operatore `[:]` non può essere utilizzato per la copia perchè effettuerebbe una copia per riferimento degli elementi annidati. In generale per effettuare una copia ricorsiva e profonda è necessario utilizzare la funzione `deepcopy()` del modulo `copy`.

Per liste annidate l'operatore `[:]` fallisce:
```py
myList = ["banana", "kiwi", "mela", [1, 2], "cachi"]
myList2 = myList[:]

myList.remove("banana")
myList2[3][0] = 12

# !!! la scrittura su myList2 ha scritto anche myList perchè la lista annidata è stata copiata per riferimento 
print(myList)  #['kiwi', 'mela', [12, 2], 'cachi']
print(myList2) #'banana', 'kiwi', 'mela', [12, 2], 'cachi']
```

## deepcopy()

Per la copia di liste e qualsiasi altro oggetto è possibile ed è consigliabile utilizzare una funzione `deepcopy()` del modulo `copy` che esegue una copia profonda quindi considera anche oggetti e liste annidate

```py
import copy

myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]
myList2 = copy.deepcopy(myList)

myList.remove("banana")

print(myList)  #['kiwi', 'mela', 'mandarino', 'cachi']
print(myList2) #['banana', 'kiwi', 'mela', 'mandarino', 'cachi']
```

La funzione `deepcopy()` è l'unica che eseegue in modo affidabile la copia di elementi considerando eventuali elementi annidati.

```py
import copy
myList = ["banana", "kiwi", "mela", [1, 2], "cachi"]
myList2 = copy.deepcopy(myList)

myList.remove("banana")
myList2[3][0] = 12

print(myList)  #['kiwi', 'mela', [1, 2], 'cachi']
print(myList2) #['banana', 'kiwi', 'mela', [12, 2], 'cachi']
```