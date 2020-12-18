---
layout: page
title: Corso Python - 17
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 17
---

## Esercizio Asta online v5

Il seguente script vuole simulare l'andamento di un'asta online con la seguente regola:
- L'asta verrà aggiudicata da chi avrà fatto un'offerta la più vicina alla media delle offerte degli altri

L'utente dovrà inserire un'offerta in *bit coin* e una *email* che rappresenterà l'identificativo. In questa quinta parte introdurremo le funzioni:

- `trova_email(email, lista_offerte)`: Riceve come parametro una stringa digitata in input dall'utente che rappresenta l'identificativo utente, *email* e la lista di tutte le offerte, *lista_offerte*. Ritorna un **boolean** *True* se trova l'identificativo *email* ricevuto come parametro come identificativo nella *lista_offerte*. Questa funzione controlla quindi se un utente ha già fatto un'offerta.

- `media_offerte(lista_offerte)`: Riceve come parametro la lista di tutte le offert *lista_offerte*, calcola la media dei valori delle offerte che rappresentano i *bit coin* e ne ritorna il valore. Ritorna quindi un valore **float**

- `minimo(lista_offerte)`: Riceve come parametro la lista di tutte le offert *lista_offerte*, calcola il minimo dei valori delle offerte che rappresentano i *bit coin* e ne ritorna il valore. Ritorna quindi un valore **float**

- `massimo(lista_offerte)`: Riceve come parametro la lista di tutte le offert *lista_offerte*, calcola il massimo dei valori delle offerte che rappresentano i *bit coin* e ne ritorna il valore. Ritorna quindi un valore **float**

```py
import re

def trova_email(email, lista_offerte):
    trovato = False

    for offerta in lista_offerte:
        if offerta[0] == email:
            trovato = True
            break

    return trovato


def media_offerte(lista_offerte):
    somma = 0.0
    for offerta in lista_offerte:
        somma += offerta[1]

    return somma / len(lista_offerte)


# si assume che la lista non sia vuota
def minimo(lista_offerte):
    #non si parte mai da un valore assoluto
    #prelevo solo il valore numerico dell'offerta
    #min è un numero float
    min = lista_offerte[0][1]

    #lista_offerte[1:] ritorna una lista dal primo elemento fino all'ultimo
    #Itero ogni elemento della lista lista_offerte a partire dal primo
    for offerta in lista_offerte[1:]:
        #se trovo un elemento più piccolo dell'attuale <min>, aggiorno min
        if offerta[1] < min:
            min = offerta[1]

    return min


# si assume che la lista non sia vuota
def massimo(lista_offerte):
    max = lista_offerte[0][1]
    for offerta in lista_offerte[1:]:
        if offerta[1] > max:
            max = offerta[1]

    return max


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
        # if nuova_offerta in offerte:
        #     print("Questo utente ha già fatto la sua unica offerta ... respinto!")
        #     continue
        # else:
        #     offerte.append(nuova_offerta)

        if trova_email(email, lista):
            print("Questo utente ha già fatto la sua unica offerta ... respinto!")
            continue
        else:
            lista.append(nuova_offerta)

    return lista

# grazie all`uso di funzioni la complessità del programma principale
# è drasticamente ridotta
offerte = inserisci_offerte()
stampa_lista(offerte)
print(f"Offerta Media: {media_offerte(offerte)}")
print(f"Offerta minima: {minimo(offerte)}")
```

![](./images/asta-05.gif)

---

<div class="next-prev">
    <a href="./py-course-15.html" id="prev-link"> previus </a> 
    <a href="./py-course-17.html" id="next-link"> next </a>
</div>