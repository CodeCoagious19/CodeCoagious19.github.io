---
layout: page
title: Corso Python - 15
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 16
---

## Introduzione alle Funzioni
Le funzioni vanno definite prima di utilizzarle

Una funzione è un blocco di codice che viene eseguito solo quando viene chiamata.
È possibile passare dei valori, chiamati **parametri**, in una funzione.

Una funzione può restituire dei valori come risultato.

In Python una funzione viene definita utilizzando la parola chiave `def`.

[w3schools - Python Functions](https://www.w3schools.com/python/python_functions.asp)

```py
#definizione di una funzione
def myFunc(param)
    #code

#chiamata di una funzione
myFunc(value1)
```

Esempio:

```py
def saluta(nome):
  print("ciao: " + nome +"!")

saluta("Emil")
saluta("Tobias")
saluta("Linus")

# ciao: Emil!
# ciao: Tobias!
# ciao: Linus!
```

## Esercizio Asta online v4

Il seguente script vuole simulare l'andamento di un'asta online con la seguente regola:
- L'asta verrà aggiudicata da chi avrà fatto un'offerta la più vicina alla media delle offerte degli altri

L'utente dovrà inserire un'offerta in *bit coin* e una *email* che rappresenterà l'identificativo. In questa quarte parte introdurremo la funzione `stampa_lista(lista_offerte)` che riceve in ingresso la lista delle offerte e stampa il risultato secondo un formato specifico e la funzione `inserisci_offerte()` che rappresenta l'acquisizione dati da tastiera da parte dell'utente e il controllo sull'integrità dei dati ricevuti. Di fatto la complessità dello script si riduce alla chiamta di due funzioni: `inserisci_offerte()` e `stampa_lista`

```py
import re

def stampa_lista(lista_offerte):
    for offerta in lista_offerte:
        print(f"Email Offerente: {offerta[0]} - Offerta: {offerta[1]} ")


def inserisci_offerte():
    lista = []
    altre_offerte = True

    while altre_offerte:
        offerta = input("Inserisci l`offerta pervenuta (0 per terminare): ")

        try:
            offerta = float(offerta)
        except ValueError:
            print("Formato non valido, riprova ...")
            continue

        if offerta == 0:
            altre_offerte = False  # USCITA DAL CICLO
            continue

        if offerta < 0:
            print("Non possono essere fatte offerte negative!")
            continue

        email = input("Inserire l`email dell`offerente: ")

        if not re.match("^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$", email):
            print("Email non valida, riprova ...")
            continue

        nuova_offerta = [email, offerta]

        # controllo valido solo se viene fatta la stessa offerta con la stessa mail ... limitato!
        if nuova_offerta in lista:
            print("Questo utente ha già fatto la sua unica offerta ... respinto!")
            continue
        else:
            lista.append(nuova_offerta)

    return lista


# grazie all`uso di funzioni la complessità del programma principale
# è drasticamente ridotta
offerte = inserisci_offerte()
stampa_lista(offerte)
```