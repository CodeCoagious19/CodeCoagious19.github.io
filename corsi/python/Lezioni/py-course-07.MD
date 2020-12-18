---
layout: page
title: Corso Python - 08
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 8
---

## Le stringe 

**Le stringhe sono un tipo di dato immutabile in python** <br>

Questo significa che la copia di stringhe può essere fatta attraverso l'assegnamento tra i nomi (contrariamente a quanto accade per altri linguaggi come C++) poichè quando viene creata una copia tramite l'assegnamento non viene copiato il riferimento della stringa ma l'intero oggetto stringa.

```py
s1 = "ciao"
s2 = s1
s2 = "ciaociao"

print(s2) #ciaociao
print(s1) #ciao
```

Ecco una dimostrazione approfondita andando ad scavare tra gli indirizzi in memoria con la funzione `id`

```py
s1 = "ciao"
print(id(s1)) #140440511029104
s2 = s1
print(id(s2)) #140440511029104
s2 = "ciaociao"
print(id(s2)) #140440511029168

print(s2) #ciaociao
print(s1) #ciao
```

**Attenzione** Eseguendo la copia `s2 = s1` ancora non si assegna ad `s2` un nuovo indirizzo in memoria per motivi di efficienza. Lo si assegna quando ad `s2` si assegna un nuovo valore

## Interpolazione di stringhe - Metodo `format()`

Il metodo `format()` applicabile alle stringhe consente di inserire espressioni valutabili all'interno di stringhe
[w3schools - Python String format() Method](https://www.w3schools.com/python/ref_string_format.asp).

Il metodo `format()` formatta i valori specificati e li inserisce all'interno del segnaposto della stringa.
Il segnaposto viene definito utilizzando le parentesi graffe: {}.

Esempio:

```py
#sintassi 1
txt = "1Kg di sale da cucina a solo {price} euro!"
print(txt.format(price = 2)) #1Kg di sale da cucina a solo 2 euro!

#sintassi 2
txt = "1Kg di sale da cucina a solo {0} euro! Rimasti {1} pezzi" 
print(txt.format(2, 500)) #1Kg di sale da cucina a solo 2 euro! Rimasti 500 pezzi
```

Esiste anche una sintassi leggermente diversa:

```py
myList = ["dentista", "17:00"]
print(f"Evento: {myList[0]} - Ora: {myList[1]} ") #Evento: dentista - Ora: 17:00 
```

---

<div class="next-prev">
    <a href="./py-course-06.html" id="prev-link"> previus </a> 
    <a href="./py-course-08.html" id="next-link"> next </a>
</div>
