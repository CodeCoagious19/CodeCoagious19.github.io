---
layout: page
title: Corso Python - 09
parent: Python
grand_parent: Corsi
has_children: false
nav_order: 9
---

## PyPDF2 - Merge All pdf v2

Questa è una versione migliorata dello script *Merge All pdf*. Aggiunge dei controlli sull'estensione del file e sulla natura del file. Controlla infatti se un file termina con formati "strani" come ".pdF", "PDf" considerandoli comunque validi e controlla eventuali falsi file trappola come cartella che termina con estensione ".pdf". <br>
Faremo uso di:

- `os.path.isfile(path+file)`: Ritorna *true* se il file specificato come parametro (eventualmente con un path relativo o assoluto) è realmente un file.
- Metodo su **stringhe** `.upper()`: Ritorna una **copia** della stringa a cui si applica il metodo in caratteri maiscoli
- **chaining** condition `and`: Permette la concatenazione di condizioni logiche. Ritorna *true* se tutte le condizioni concatenate sono *true*  

Script completo e migliorato

```py
import PyPDF2
import os

print("**********************************************")
print("Unisco i file pdf presenti in questa directory")
print("**********************************************")

listaFiles = os.listdir()

for nomeFile in listaFiles:
    if nomeFile.endswith('.pdf'):
        print(nomeFile)
print('\n')

#chiedo all'utente come vuole chiamare il file di output
print("Salvo il risultato con il nome:")
nomeFileDestinazione = input()
#Apro il file in scrittura binaria
PDF_Destinazione = open(nomeFileDestinazione, "wb")
print('\n')

merger = PyPDF2.PdfFileMerger()
print("Elaborazione di..")
for nomeFile in listaFiles:
    #Elaboro solo i file con estensione ".pdf" o "PDF" o "PdF" ..
    if os.path.isfile(nomeFile) and nomeFile.upper().endswith('.PDF'):
        #stampo il nome del file
        print(nomeFile)
        #lo apro in lettura binaria
        pdfFileInput = open(nomeFile, "rb")
        #creo un'istanza della classe <PdfFileReader> sul file appena aperto
        PDF_Reader = PyPDF2.PdfFileReader(pdfFileInput)
        #Appendo il file PDF in coda all'oggetto merger
        merger.append(PDF_Reader)
        #chiudo il file aperto
        pdfFileInput.close()
print('\n')

#Operazione di scrittura
print("Scrittura su: " + nomeFileDestinazione)
merger.write(PDF_Destinazione)
PDF_Destinazione.close()

print("Finito..")
```

## Introduzione alla manipolazione dei docx

Con il seguente script inizieremo a manipolare i docx
Da terminale puoi installare il modulo per la manipolazione dei docx con il comando:

```bash
pip install python-docx
```

Importa il modulo "python-docx" all'interno del tuo script con:
```py
import docx
```

La documentazione ufficiale del modulo "python-docx" la puoi trovare su [docx - documentazione](https://python-docx.readthedocs.io/en/latest/).

Del modulo "python-docx" utilizzeremo:

- `docx.Document(docxFile)`: Chiama il costruttore della classe `Document` passando come parametro di inizializzazione il file "docx" che intendiamo elaborare. Ritorna un'istanza della classe `Document`

- Metodo `sections` della classe `Document`: applicato a un'istanza della classe `Document` restituisce le sezioni del documento "docx"-

- Metodo `paragraphs` della classe `Document`: applicato a un'istanza della classe `Document` restituisce una **lista dell'oggetto** `Paragraph`

- Metodo `text` della classe `Paragraph`: applicato a un'istanza della classe `Paragraph` restituisce il testo di un paragrafo

Utilizzeremo anche l'operatore `*` su **stringa** che permette di generare una ripetizione della stringa a cui si applica l'operatore.

```py
print("ciao "*2 + "!") #ciao ciao !
```

Script completo:

```py
#Manipolazione docx
import docx

divina = docx.Document("divina1.docx")

sezioni = divina.sections

print("il documento contine:")

#Utile quando ci sono diversi valori da valutare
print("- {0} sezioni".format(len(sezioni))) #altrenativa >>> print(str( len(sezioni) ) + " sezioni" ) 


paragrafi = divina.paragraphs
print("- {0} paragrafi".format(len(paragrafi))) #4 sezioni

print("\nStampo i paragrafi..")
print("-"*50)
#Per ogni elemento p estratto dalla lista paragrafi..
for p in paragrafi:
    #p.text restituisce il testo di un paragrafo
    print(p.text)
    #questo metodo su stringa genera una ripetizione 
    print("-"*50)
```

---

<div class="next-prev">
    <a href="./py-course-07.html" id="prev-link"> backa> 
    <a href="./py-course-09.html" id="next-link"> next </a>
</div>
