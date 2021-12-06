# Uvod u nakladništvo i knjižarstvo

u akad. god. 2021./2022.

Nakladništvo je najrašireniji posao u svijetu

## Uvod u GIT za nakladnike

# Uvod u Git repozitorije

---

## Što je Git?

Kontrola verzija se koristi kod održavanja većeg broja različitih verzija izvornoga koda. Ovaj pristup omogućava praćenja promjena u kodu tijekom dužeg vremenskog perioda. Kontrola verzija osim navedenog omogućva suradnju među većim brojem osoba koje se mogu nalaziti na različitim lokacijama, te slanje izvornog koda s lokalnog uređaja na testni, a potom i na produkcijski server. 

---

## Git omogućava sljedeće: 

- praćenje promjena u kodu
- sinkronizaciju koda među različitim korisnicima
- testiranje promjena u kodu bez gubitka originala
- vraćanje starijih verzija koda

---

## Instalacija Git-a

Prvo provjerite na svom računalu da li je Git već instaliran – command line na Windowsima ili terminal na Mac/Linuxu.

```
git --version
git version 2.29.2
```
Ako Git nije instaliran, otvorite [Git-SCM](https://git-scm.com/downloads/) i preuzmite izvršnu datoteku za instalaciju sustava na vaše računalo.

---

## Pokretanje Git-a

Instalacijom Git-a moguće je svaki direktorij na lokalnom računalu pretvoriti u tzv. repozitorij pomoću kojeg je moguće pratiti promjene u projektu. 

Nakon uspješne instalacije Git-a provjerite pomoću `which` naredbe da li je izvršni program uspješno instaliran. 


```
$ which git

/usr/local/bin/git

```

---

Nakon toga potrebno je postaviti *globalne* postavke (jednokratno na svakom računalu). 

```
$ git config --global user.name "Vaše ime"

$ git config --global user.email vas.email@primjer.com
```
Ove postavke su vrlo bitne ako surađujete s nekim na projektu.

---

### Vježbe

1. U CLI-u pokrenite `git help` naredbu. Koja naredba je prva navedena?
2. Ako vam je `git help` naredba izbacila previše sadržaja, sugeriram prebacivanje *outputa* u `less` naredbu. Podsjećam da se za pipe opciju koristi simbol `|`.
3. Git pohranjuje globalne postavke u skrivenu datoteku koja se nalazi u vašem home direktoriju. Provjerite sadržaj `~/.gitconfig` datoteke pomoću neke od naredbe (`cat`, `less`) ili u nekom uređivaču teksta (npr. nano, Notepad++, VSC, Atom, ...)-. 

---

## Inicijalizacija repozitorija

Na nekom mjestu otvorite direktorij `Repos`, a u sljedećem koraku ćemo otvoriti novi direktorij `web`. 

```
$ mkdir -p repos/web
```
Podsjećam da `mkdir` naredba otvara novi direktorij, a argument `-p` otvara prema potrebi "međudirektorije" (u konkretnom slučaju otvara direktorij `Repos`)

Locirajte se pomoću `cd` naredbe u novootvoreni direktorij `web` i izlistajte sadržaj direktorija.

```
$ cd Repos/web
$ ls
```
Direktorij je, naravno, potpuno prazan!

---

Spremni smo za inicijalizacija novog repozitorija unutar web direktorija. Sve naredbe započinju s `git` nakon čega slijedi naziv sljedećeg koraka (npr. lokalni repozitorij otvaramo pomoću `init`). 

```
$ git init
Initialized empty Git repository in /Users/fbox0920/Repos/web/.git/
$ web git:(master) 
```
Dobili smo nekoliko povratnih informacija, a između ostalog naziv zadane Git grane (eng. *branch*) koja se u ovom slučaju naziva `master`. Uskoro ćemo više saznati o granama i grananju. 

---

### Vježba

1.	Pokrenite naredbu `ls -a` (discussedza ispis svih datoteka i direktorija u novootvorenom lokalnom repozitoriju. Kako glasi naziv skrivene datoteke koja je izrađena kod pokretanja repozitorija? 
2.	Otvorite skriveni direktorij i pomoću `cat` naredbe istražite i na zaslonu prikažite konfiguracijske postavke. 

---

## Prvi commit

Prazan repozitorij nema smisla, pa ćemo izraditi jednu jednostavnu web stranicu koju ćemo prema konvenciji imenovati `index.html`. Novu web stranicu možemo izraditi na nekoliko načina. Možete li navesti kako?

```
$ touch index.html
```
Nakon što smo izradili prvu datoteku možemo koristiti `git status` naredbu. 
```

$ touch index.html

On branch master
No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	index.html

nothing added to commit but untracked files present (use "git add" to track)
```
Iz poruke je razvidno da se `index.html` datoteka trenutno ne prati (engl. untracked), tj. da Git još uvijek ne zna za njezino postojanje. Stoga ćemo ju dodati pomoću `git add` naredbe. 
```
$ git add index.html
```
ako želimo dodati samo jednu konkretnu datoteku ili 
```
$ git add -A
```
`-A` za dodavanje svih (ALL) datoteka koje Git trenutno ne prati (umjesto `-A` možemo koristiti i `git add .` kako bismo u sustav praćenja dodali sve datoteke iz trenutnog radnog direktorija). 

Provjerite rezultat `git add -A` naredbe tako da unesete `git status`. 
```
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   index.html
```
Pojam “unstage” implicira da je datoteka promaknuta iz statusa "untracked" u status "staged" što znači da je datoteka spremna za dodavanje u repozitorij. Untracked/Unstaged i Staged su dva od ukupno četiri Git statusa. 

![Git status](img/slika1.png)

---

Nakon što smo dodali promjene u tzv. "staging" područje možemo sve postaviti kao dio repozitorija korištenjem `git commit` naredbe koja se najčešće koristi s opcijom `-m` koja uključuje poruku s opisom svrhe ili promjene. 
```
$ git commit -m "pokretanje repozitorija"
[master (root-commit) c08900b] pokretanje repozitorija
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 img/slika1.png
 create mode 100644 index.html
```

---

Rezultat `commit` naredbe možete provjeriti u `git log` zapisu: 

```
commit c08900bc25ce820dbd1af014afc5d798c2eea1b9 (HEAD -> master)
Author: fpehar <fpehar@unizd.hr>
Date:   Thu Nov 19 13:58:59 2020 +0100

    pokretanje repozitorija
``` 
Svaki `commit` se identificira pomoću hash-a – jedinstvenog niza alfanumeričkih znakova. `Hash` se često naziva i `"SHA"` (izgovara se shah; *Secure Hash Algoritham*). 

---

### Vježba
1.	Koristeći touch naredbu izredite u svojm repozitoriju prazne datoteke koje ćete nazvati `foo` i `bar`.
2.	Koristeći `git add foo` dodajte `foo` u tzv. staging područje. Pomoću `git status` provjerite rezultat. 
3.	Koristeći `git commit -m` dodajte poruku i dodajte `foo` u repozitorij. 
4.	Koristeći `git add bar` dodajte `bar` u staging područje. Potvrdite rezultat s `git status` naredbom.  
5.	Sad pokrenite `git commit` bez `-m` opcije. Koristeći `vi` uređivač teksta dodajte poruku "dodan bar", pohranite i izađite iz aplikacije.
6. Pomoću `git log` potvrdite uspješnost prethodnih koraka.

---

## Diff prikaz

Koristeći `echo` naredbu dodajte tekst "hello, world" `index.html` datoteci. 
``` 
echo "hello, world" > index.html 
``` 
Pomoću unix naredbe `diff` provjerite razliku između `foo` i `bar`. 

---

## GitHub: udaljeni repozitorij

GitHub je mrežno sjedište koje omogućava pohranu Git repozitorija na internetu. Git omogućava upravljanje privatnim i javnim repozitorijima koji se mogu dijeliti s drugih korisnicima. 

GitHub Pro je besplatan za sve studente, te nudi brojne dodatne pogodnosti. Studentski račun možete otvoriti na sljedećoj adresi: 
[https://education.github.com/students](https://education.github.com/students)
ili 
[https://education.github.com/discount_requests/student_application](https://education.github.com/discount_requests/student_application)

Studentski račun vam, Između ostalog, omogućava neograničenu objavu privatnih repozitorija koji nisu dostupni neautoriziranim korisnicima. 

---

## Otvaranje novog repozitorija
- Otvorite [github](https://github.com/)
- Logirajte se u svoj račun
- Odaberite gum [novi repozitorij](https://github.com/new) – otvorit će vam se opcija za inicijalizaciju novog repozitorija s `README` datotekom, ali ovaj put možete preskočiti izradu navedene datoteke. 
- Odaberite gumb `Create repository`

---

## Udaljeni repozitorij

Izradite novi online repozitorij kako biste mogli poslati (push) sadržaj iz lokalnog repozitorija na Github. 

``` 
$ git remote add origin https://github.com/fpehar/web.git
$ git push -u origin master
```

---

## Dodavanje README.md datoteke

Idemo vježbati `add`, `commit` i `push` naredbe. Lokalno u web/ direktoriju izradite README.md datoteku u koju ćete unijeti 6 odlomaka teksta prezuetih s Lorem Ipsum generatora teksta. U oblikovanju teksta koristite Markdown oznake (h1, h2, h3, slika, URL, numerirani popisi, nenumerirani popisi, i sl. 

Dodajte, postavite i pošaljite README.md datoteku u vaš online GitHub repozitorij. Poveznicu do README.md datoteke unesite u moj repozitorij dostupan na adresi: https://github.com/fpehar/ATP2021. Otvorite direktorij studenti i u datoteku studenti.md upište URL adresu vašeg online repozitorija koristeći "Edit this file" opciju. 

---

# Popis i opis osnovnih Git naredbi

**git init**

> Zamislite da ste od kolege primili mail s nekim bitnim podacima, dokumentima ili kodom. Sve što trebate u tom trenutku učiniti jest sljedeće: 
> 1. otvorite na lokalnom računalu novi direktorij (npr. `mkdir test`)
> 2. pozicionirajte se u navedeni direktorij (npr. `cd test`)
> 3. unesite naredbu `git init`
> 4. unesite kod ili izradite novu datoteku (npr. `nano README.md`)


