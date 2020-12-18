---
layout: page
title: Corso Python - 06
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 6
---

## Liste

Abbiamo già visto implicitamente un'introduzione al tipo lista e in particolare come creare e iterare sugli elementi di una lista attraverso il ciclo `for` e la funzione `range()`. Il tipo dato lista è molto importante nel linguaggio python.

Le liste sono un tipo di dato utilizzato per memorizzare diversi elementi in una singola variabile.

Le liste sono uno dei 4 tipi di dati incorporati in Python utilizzati per memorizzare raccolte di dati, gli altri 3 sono Tuple, Set e Dictionary, tutti con qualità e utilizzo diversi.

Vediamo le caratteristiche principali delle liste:

- Le liste possono contenere qualsiasi tipo di dato
- Gli elementi della lista sono indicizzati, il primo elemento ha indice [0], il secondo elemento ha indice [1] .. A differenza della maggior parte dei linguaggi si possono usare anche indici negativi, [-1] si riferisce all'ultimo elemento, [-2] si riferisce al penultimo elemento ecc.
- Gli elementi in una lista sono ordinati e l'ordine è stabilito dall'indice. 
- Dopo la creazione, è possibile aggiungere elementi, cambiare il valore degli elementi già esistenti o rimuoverli 
- Dal momento che le liste sono indicizzate è possibile avere elementi duplicati
- La funzione `len()` ritorna il numero degli elementi presenti in una lista
- L'operatore `[::]` permette lo *slicing* di liste ovvero la creazione di porzioni di liste a partire dalla lista a cui si applica l'operatore `[::]`

[w3schools - Python Lists](https://www.w3schools.com/python/python_lists.asp)


## Accesso agli elementi di una lista

L'accesso agli elementi di una lista si effettua tramite l'operatore `[]`
```py
#indici     0         1       2       3            4
#indici    -5        -4      -3      -2           -1
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]

print(myList[2])  #mela
print(myList[-1]) #cachi

print(len(myList)) #5
```

## Modifica del valore degli elementi in una lista.

Per cambiare il valore degli elementi in una lista si utilizza l'operatore `[]` 

```py
#indici     0         1       2       3            4
#indici    -5        -4      -3      -2           -1
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]

myList[-1] = "arancia"
myList[2] = "pera"
print(myList)

myList[1:3] = ["mandorla", "nocciola"] 
print(myList)
```

## Aggiunta di elementi in una lista

Sono disponibili i metodi:

- `append(elem)`: Appende *elem* in coda alla lista
- `insert(index, elem)`: Inserisce (senza nessun replace) *elem* alla posizione *index* facendo scalare di una posizione gli elementi dalla posizione *index*
- `extend(otherList)`: Appende in coda gli elementi della lista passata come parametro, *otherList* 

```py
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]
myList2 = ["mandorla", "nocciola", "noce"]

myList.append("anguria")
print(myList) #['banana', 'kiwi', 'mela', 'mandarino', 'cachi', 'anguria']

myList.insert(2, "melone")
print(myList) #['banana', 'kiwi', 'melone', 'mela', 'mandarino', 'cachi', 'anguria']

myList.extend(myList2)
print(myList) #['banana', 'kiwi', 'melone', 'mela', 'mandarino', 'cachi', 'anguria', 'mandorla', 'nocciola', 'noce']
```

## Rimozione di elementi in una lista

Sono disponibili i metodi:

- `remove(elem)` : Toglie *elem* dalla lista
- `pop(?index)`: Toglie l'elemento corrispondente all'indice *index* passato come parametro opzionale. Se non viene passato nessun parametro toglie l'ultimo elemento. E' possibile ottenere questo risultato anche con il comando `del`, specificando l'elemento, `del myList[index]`
- `clear()`: Svuota la lista. La lista esiste ma è vuota. E' possibile ottenere questo risultato anche con il comando `del` specificando il nome della lista `del myList` ma in questo caso elimina anche l'identificatore

```py
myList = ['banana', 'kiwi', 'melone', 'mela', 'mandarino', 'cachi', 'anguria', 'mandorla', 'nocciola', 'noce']

myList.remove("mandarino")
print(myList) #['banana', 'kiwi', 'melone', 'mela', 'cachi', 'anguria', 'mandorla', 'nocciola', 'noce']

myList.pop(2)
print(myList) #['banana', 'kiwi', 'mela', 'cachi', 'anguria', 'mandorla', 'nocciola', 'noce']
myList.pop()
print(myList) #['banana', 'kiwi', 'mela', 'cachi', 'anguria', 'mandorla', 'nocciola']
del myList[0] 
print(myList) #['kiwi', 'mela', 'cachi', 'anguria', 'mandorla', 'nocciola']

myList.clear() 
print(myList) #[]

myList = ['banana', 'kiwi', 'melone', 'mela', 'mandarino', 'cachi', 'anguria', 'mandorla', 'nocciola', 'noce']
del myList
print(myList) #NameError: name 'myList' is not defined
```

## Creazione di sotto liste, **slicing** <br>

Sintassi:<br>
`mySubList = myList[?startIndex: ?endIndex: ?Step]`: Ritorna una sotto lista a partire dalla lista a cui si applica lo slicing (*myList*). L'operatore `[]` può ricevere tre parametri opzionali separati da `:`. Il primo rappresenta l'indice di partenza (incluso), il secondo l'indice di fine (non incluso) e il terzo il passo. Se il primo parametro non è specificato si assume `0` come valore di partenza. Se il secondo parametro non è specificato si assume `len(myList) - 1` come valore di fine cioè l'ultimo elemento della lista. Se il terzo parametro non è specificato si assume un incremento positivo unitario

```py
#indici     0         1       2       3            4
#indici    -5        -4      -3      -2           -1
myList = ["banana", "kiwi", "mela", "mandarino", "cachi"]

mySubList = myList[1:]
print(mySubList)  #['kiwi', 'mela', 'mandarino', 'cachi']
mySubList = myList[-2:]
print(mySubList) #['mandarino', 'cachi']

mySubList = myList[2:4]
print(mySubList) #['mela', 'mandarino']

mySubList = myList[::2]
print(mySubList) #['banana', 'mela', 'cachi']

#Restituisce una copia <non profonda> di una lista
#Non valido per liste annidate
mySubList = myList[:]
print(mySubList) #["banana", "kiwi", "mela", "mandarino", "cachi"]

#Ordinamento inverso
mySubList = myList[::-1] 
print(mySubList) #['cachi', 'mandarino', 'mela', 'kiwi', 'banana']
```

---

<div class="next-prev">
    <a href="./py-course-04.html" id="prev-link"> previus </a> 
    <a href="./py-course-06.html" id="next-link"> next </a>
</div>