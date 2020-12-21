---
layout: page
title: Corso Python - 14
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 14
---

## Esercizio Asta online v2

Il seguente script vuole simulare l'andamento di un'asta online con la seguente regola:
- L'asta verrà aggiudicata da chi avrà fatto un'offerta la più vicina alla media delle offerte degli altri

L'utente dovrà inserire un'offerta in *bit coin* e una *email* che rappresenterà l'identificativo. E' consentita un'unica offerta per utente! In questa seconda parte ci occuperemo di inserire dei controlli aggiuntivi dei dati acquisiti.

- Aggiungeremo la possibilità di inserire numeri decimali "floating point". Per far ciò utilizzeremo la funzione di conversione esplicita da stringa (l'input da tastiera) a numero decimale, `float()`

- Rileveremo tutti gli errori legati ad un'inserimento di un dato `float` non valido come una stringa o qualche altro carattere (come ad esempio **Invio**) non interpretabile come numero decimale. Alla rivelazione dell'errore stamperemo il messaggio d'errore `"Formato non valido, riprova .."`. Utilizzeremo il costrutto `try-except`

- Aggiungeremo un'espressione regolare abbastanza semplice per il controllo del formato dell'email. Per far ciò utilizzeremo la funzione `re.match(regExp, myVar)` del modulo `re`. L'espressione regolare controlla se la stringa (nel nostro caso l'email) inizia `^` con la sequenza di caratteri minuscoli `"a-z"`, maiuscoli `"A-Z"` o numerici `"0-9"` ripetuti. E' seguita dal carattere `@`, continua con la sequenza di caratteri minuscoli, maiuscoli o numerici, prosegue con il carattere `.` ed p seguita dal dominio che per noi sarà nuovamente una sequenza di caratteri minuscoli, maiuscoli o numerici.

```py
import re
offerte = []
altre_offerte = True

while altre_offerte:
    offerta = input("Inserisci l`offerta pervenuta (0 per terminare): ")

    try:
        offerta = float(offerta)
    except ValueError:
        print("Formato non valido, riprova ...")
        continue

    if offerta == 0:
        altre_offerte = False
        continue

    if offerta < 0:
        print("Non possono essere fatte offerte negative!")
        continue

    email = input("Inserire l`email dell`offerente: ")

    if not re.match("^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$", email):
        print("Email non valida, riprova ...")
        continue

    nuova_offerta = [offerta, email]


print(offerte)
```

![](./images/asta-03.gif)

---

<div class="next-prev">
    <a href="./py-course-12.html" id="prev-link"> back </a> 
    <a href="./py-course-14.html" id="next-link"> next </a>
</div>