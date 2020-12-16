---
layout: page
title: Corso Python - 10
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 9
---

## Esercizio Asta online v1

Il seguente script vuole simulare l'andamento di un'asta online con la seguente regola:
- L'asta verrà aggiudicata da chi avrà fatto un'offerta la più vicina alla media delle offerte degli altri

L'utente dovrà inserire un'offerta in *bit coin* e una *email* che rappresenterà l'identificativo. E' consentita un'unica offerta per utente! In questa prima parte ci occuperemo dell'acquisizione dati da tastiera e della generazione di una struttura dati adeguata.


```py
offerte = []

#dato booleano di controllo ciclo
altre_offerte = True

while altre_offerte:
    #offerta contiene l'offerte in bitcoin
    offerta = input("Inserisci l`offerta pervenuta (0 per terminare): ")

    #Converto il dato ricevuto da tastiera in intero
    offerta = int(offerta)

    #Il valore "0" è il terminatore
    if offerta == 0:
        altre_offerte = False
        continue

    
    if offerta < 0:
        print("Non possono essere fatte offerte negative!")
        continue

    #Se l'offerta supera i controlli chiedo l'email
    email = input("Inserire l`email dell`offerente: ")

    #Inserisco la coppia email-offerta nella lista delle offerte
    offerte.append([email, offerta])

print("Le offerte valide sono:")
print(offerte)
```

![](./images/asta-01.gif)

Che cosa succede se l'utente inserisce dei valori di input non atesi? Ad esempio, invece che inserire un numero inserisce una stringa o qualche carattere non previsto?

![](./images/asta-02.gif)

Vedremo nel capito successivo come trattare questi errori tramite il costrutto `try Except`