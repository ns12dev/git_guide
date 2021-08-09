

  
  

## Git - No panic guide

**Introduzione**

Questa guida è pensata per agevolare la formazione delle risorse sull'utilizzo di GitHub. <br/>
La risorsa in questione dovrà comunque affiancare questi comandi ad un corretto utilizzo della piattaforma, in particolare è fortemente consigliato
caricare le modifiche sul proprio branch il più possibile per evitare perdite di codice accidentale (minimo un commit a giorno).

**Struttura della repository**

La struttura utilizzata è la seguente:

*master<br/>*
*sviluppo_intermedio<br/>*
*sviluppo_risorsa1<br/>*
*sviluppo_risorsa2<br/>*
*etc...<br/>*

Il branch personale deve rimanere tale, per condividere il codice con le altre risorse è presente il branch intermedio.<br/>Sul branch intermedio inoltre vanno
caricate versioni di codice stabili, testate, funzionanti e senza conflitti.
Sul branch master invece vanno caricate le versioni da consegnare al cliente, opportunamente testate e segnalate da un tag.

----

**Clonare una repository da ssh:gitbox**                               
*Prima di clonare la repository chiedi al tuo responsabile i permessi in lettura e scrittura.*

Controlla i progetti ai quali sei stato assegnato, poi clona il progetto.
````
ssh gitbox

git clone gitbox:/.../your_project/...
````
----

**Crea il tuo branch personale partendo da intermedio**                            
*Se non esiste intermedio crea sia il tuo branch che quest'ultimo a partire da master/main.*


````
git fetch

git checkout sviluppo_intermedio

git checkout -b your_branch

````
----

**Controlla se sono presenti degli aggiornamenti**                                               
*NB se stai lavorando sul tuo branch ma vuoi comunque prendere i nuovi aggiornamenti committali oppure mettili in stash*


Controlla se ci sono aggiornamenti su intermedio.
````
git fetch 
````
Pull & risolvi i conflitti se presenti.
````
git pull origin sviluppo_intermedio
````
Push degli aggiornamenti sul tuo branch remoto.
````
git push origin your_branch
  ````

----
  

**Push degli aggiornamenti sul tuo branch**

Controlla prima se sono presenti aggiornamenti che non vuoi includere nel push. 
````
git status
````
Se vuoi aggiungere tutti i file:
````
git add *
````
Altrimenti aggiungi uno ad uno i files che vuoi caricare.
````
git add file1 file2 file3
````
Infine esegui un commit e il push delle modifiche.
````
git commit -m "commit"

git push origin your_branch
````

----
  

**Push degli aggiornamenti sul branch intermedio**

````
git add *

git commit -m "commit"

git push origin your_branch
````
Controlla se ci sono aggiornamenti, in questo caso fai prima un pull, push  e merge sul tuo branch risolvendo i conflitti.
````
git fetch

git pull origin intermediate_branch

git push origin your_branch
````
Una volta che sul tuo branch è presente una versione stabile del merge esegui un push delle modifiche prima sul tuo branch (che dovrebbe essere senza conflitti a questo punto) e poi su intermedio ***ricordati di tornare sul tuo branch!***
````
git checkout intermediate_branch 

git pull origin your_branch 

git push origin intermediate_branch 

git checkout your_branch
 ````

----

  

**Carica le modifiche in stash**  
*Questa è una pratica molto comoda per poter mettere da parte gli sviluppi per eseguire pull oppure eseguire dei test e spostarsi su diversi branch senza eseguire un push completo*
<br>
````
git stash
````
 
**Recupera le modifiche in stash**

````
  git stash apply
````

**Tag dello sviluppo**
*Questa pratica serve a delineare un code versioning del prodotto, solitamente va taggato lo sviluppo pre-rilascio sul branch master*
````
git tag -a vX.Y -m "my version X.Y"

git push origin vX.Y oppure

git push origin --tags
````


  

## Questa sezione è informativa per lo sviluppo personale.

**Setup globale di Git**  
````
git config --global user.name "your-username"

git config --global user.email "your-mail@email.com"
````
  
----

  

**Create a new repository**  
*Per sviluppi personali, in azienda devi chiedere al tuo responsabile*
<br>
````
git clone https://gitlab.com/.../repo.git

cd repo

touch README.md

git add README.md

git commit -m "add README"

git push origin main

````

----

  

**Carica un progetto esistente su Git**
````
cd existing_repo

git remote rename origin old-origin

git remote add origin https://gitlab.com/.../repo.git

git push origin --all

git push origin --tags
````
