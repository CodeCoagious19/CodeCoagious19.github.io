---
layout: page
title: Corso Python - 10
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 10
---

## Python `while()`

Con il ciclo while possiamo eseguire un insieme di istruzioni fintanto che una condizione è vera.

[w3schools - Python While Loops](https://www.w3schools.com/python/python_while_loops.asp)

Sintassi:

```py
while condition:
    #code
```

Esempio:

```py
i = 1
while i < 6:    #1 < 6, true   #2 < 6, true   #3 < 6, true   #4 < 6, true    #5 < 6, true    #6 < 6, false -> exit
    print(i)    #1             #2             #3             #4              #5                
    i = i + 1   #i = 2         #i = 3         #i = 4         #i = 5          #i = 6          

# 1
# 2
# 3
# 4
# 5
```

## Comando `break`

Con l'istruzione `break` possiamo interrompere il ciclo anche se la condizione while è vera:

Sintassi:

```py
while condition:
    #code
    #code
    #..
    break #esce
```

Esempio:

```py
i = 1
while i < 6:    #1 < 6, true   #2 < 6, true   
    print(i)    #1             #2                          
    i = i + 1   #i = 2         #i = 3         
    if i == 3:  #i = 2, false  #i = 3, true -> exit
        break
            
# 1
# 2
```

Con i cicli c'è sempre da tenere in considerazione **quando** viene effettuato il controllo delle condizioni di uscita ed entrata del ciclo e la sequenza con cui vengono eseguite le istruzioni all'interno del ciclo. Leggendo l'esempio di sopra non è chiaro se il programmatore con la condizione `i == 3` vuole che venga stampato il numero `3` oppure no. Un'ottima strategia è quella di inserire tutte le condizioni di uscita del ciclo all'inizio ed eventuali istruzioni di controllo ciclo alla fine. Al centro del ciclo andranno tutte le istruzioni che verranno eseguite nel caso *standard*

```py
i = 1
while i < 6:    #1 < 6, true   #2 < 6, true   #3 < 6
    #Condizione di uscita ciclo
    if i == 3:  #i = 1, false  #i = 2, false  #i = 3, true -> exit
        break  
    print(i)    #1             #2     
    #Condizione di controllo ciclo                     
    i = i + 1   #i = 2         #i = 3         
            
# 1
# 2
```

## Comando `continue`

Con l'istruzione `continue` possiamo interrompere l'iterazione corrente e continuare con la successiva

Sintassi:

```py
while condition:
    #code
    #code
    #..
    continue #esce
```

Esempio

```py
i = 1
while i < 6:                 #1 < 6, true   #2 < 6, true   #3 < 6, true   #4 < 6, true   #5 < 6, true   #6 < 6, false -> exit
    if i == 3:               #i = 1, false  #i = 2, false  #i = 3, true   #i = 4, false  #i = 5, false 
        print("Numero " + i)                               #Numero 3
        i = i + 1                                          #i = 4
        continue                                           #execute
    print(i)                 #1             #2                            #4             #5                   
    i = i + 1                #i = 2         #i = 3                        #i = 4         #i = 5         #i = 6         
            
# 1
# 2
# Numero 3
# 4
# 5
```

## Alcune considerazioni finali

Python ha due comandi di loop primitivi:

- `while` loop
- `for` loop

E' normale chiedersi quando usare uno e quando usare l'altro.. Riporto quindi una serie di caratteristiche dei due cicli iterativi in Python

- `for` loop è un ciclo enumerativo. Andrebbe utilizzato quando è noto a priori il numero di iterazioni totali
- `while` loop è un ciclo indefinito. Andrebbe utilizzato quando non è noto a priori il numero di iterazioni totali
- I comandi `break` e `continue` possono essere utilizzati indistintamente sia sul ciclo `for` che sul ciclo `while`

---

<div class="next-prev">
    <a href="./py-course-08.html" id="prev-link"> back </a> 
    <a href="./py-course-10.html" id="next-link"> next </a>
</div>