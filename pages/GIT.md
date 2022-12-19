# SADRZAJ
[START](#start)  
[STAGING](#staging)  
[UNSTAGE](#unstage)  
[STATUS](#status)  
[COMMIT](#commit)  
[LOG](#log)  
[RESTORE COMMIT](#restore-commit)  
[ORIGIN / MASTER](#origin-master)  
[REMOTE REPOSITORIES](#remote-repositories)  
[STASH](#stash)  
[GRANE](#grane)  
[FAJL .gitignore](#fajl-gitignore)  
[manje bitne stvari](#manje-bitne-stvari)  
[Novi repozitorijum, github uptstva](#novi-repozitorijum-github-uptstva)  
[GIT PAGES](#git-pages)  
[Errors](#errors)

> Lep tutor na srpskom: https://www.webprogramiranje.org/git-komande/  

## VS Code shortcut
csP (command Palete)> git clone 

## PRAVLJENJE NOVOG GIT-a
1. napravim folder na kompu, koji cu da bacim na git. RMB> "Git Bash here".
2. touch .gitignore index.html style.css app.js 
3. git init
```sh
   3.1 git config --global user.name 'djlabat' (ovo se radi samo prvi put na novom kompu)
   3.2 git config --global user.email 'djlabat@gmail.com' (samo prvi put na novom kompu)  
```



## START
`git INIT`       // od vec stvorenog foldera na kompu pravi se repository na Git  

## STAGING
`git ADD` <file> // to INCLUDE what will be committed. What will be on staging area  
`git ADD *.html` // dodaje sve *.html fajlove  
`git ADD .`		 // *.*  

## UNSTAGE
`git RM <file>`          // unstage and DELETE from hard disk. Nije dovoljno samo rucno obrsati fajlove, nego moraju se i unstage. Zato je ova komanda super.   
`git RM --cached <file>` // UNSTAGE, to exclude what will be committed  
`git RM -f <file>`   // DELETE izmenjenih fajlova.  

## STATUS
`git STATUS `    // Prikaz statusa fajlova, da li su dodati na listu za commit (ako jesu, onda su staged - zeleni) ili ne (crveni), da li su se promenili (modified) ili ne (nema ih). Ako se pokrene STATUS a ne vidi se nista onda znaci da nista nije promenjeno od poslednjeg commit-a. Kad se nesto izmeni, u statusu ce da se pojavi (modified). Ako nije ADD-ovan onda ce pisati da je izmenjen ali nije staged. Sto znaci da posle svakog COMMIT-a moraju fajlovi nanovo da se dodaju pre novog commit-a, bilo da su promenjeni ili ne, mada ako nisu promenjeni onda nema ni razloga da se dodaju.  


## COMMIT
`git COMMIT `    // fajlovi koji su oznaceni kao STAGED (pomocu komande ADD) se snimaju na Git. Kada se pokrene komanda otvara se "Vim" edior, ali da bi se nesto uradilo moram pritisnuti "I" da bi usao u insert mode. Potom kucam "opis" promene. U VIM edtoru, linije koje pocinju sa "#" su nevazece linije, a linije bez icega ce uci u commit "opis". Na kraju, pritisnem "ESC", pa kucam ":wq" (write-quit), enter. Dobijamo info o promenama.  
`git COMMIT -m "Ovde ide text o promenama."` // jednostavniji nacin.  
`git COMMIT --amend` // dopuna poslednjeg commita novim izmenama.  

## LOG
`git LOG`   // izlista ti sve komite do sada  

## RESTORE COMMIT
`git RESET --hard 456df89a`  // Vracanje na stanje nekog prethodnog komita  
`git RESET --hard`          // bez koda, resetuje trenutni git  
`git CHECKOUT 146fa46a`  // Prebacivanje u neki drugi (prethodni) komit, pri cemu se cuva sadasnji  

## ORIGIN - MASTER  
`origin` - je alias za punu URL adresu online repozitorijuma (npr. https://url_link_udaljenog_repozitorijuma). Ovakvo skraćeno predstavljanje URL-a nam omogućava jednostavniji rad sa naredbama jer izbegavate da koriste ogroman URL svaki put kada vam je u naredbi potreban. Koji tačno link predstavlja ovaj alias može se proveriti sa naredbom: `git remote -v`  

`master` - grana (branch).
Kada se u nekim naredbama pominje neka GRANA (npr. master) na UDALJENOM REPOZITORIJUMU potrebno je pored imena grane dodati i link do udaljenog repozitorijuma npr:  

```js
git push    https://url_link_udaljenog_repozitorijuma    master
```

Znajući da je "origin" alias za ovaj link, sada se "master" grana na udaljenom repu može označiti jednostavnije sa “origin master”. Pa bi komanda iz prethodnog primera izgledala ovako:  

```js
git push  origin  master
```
   
## REMOTE REPOSITORIES  
git remote -v
`git REMOTE add origin http://nasserver.git` // URL Adresa `http://nasserver.git` udaljenog servera je stavljena u konstantu "origin".  
`git PUSH origin master` // push-uj na udaljeni server (Remote Repository) `http://nasserver.git`, granu "master".  
`git REMOTE remove` // uklanjanje repozitorijuma  
`git PULL`    // skida sadrzaj sa udaljenog repozitorijuma i/ili odmah azurira lokalni repozitorijum sa verzijom koja je na udaljenom repozitorijumu.  
`git CLONE https://github.com/mdbootstrap/knowledge-base.git` // skidanje nekog (tudjeg) Git projekta na svoj komp. Adresu skinuti sa gitHub sajta.  

## STASH
`git STASH` // sprema se (lokalno) trenutno stanje radnog direktorijuma (bez commit) da bi mogao da se prebacima na rad na necem drugom. Nakon spremanja projekat se vraca na stanje poslednjeg commita.  
`git STASH list` // lista svih spremljenih stash izmena  
`git STASH apply stash@{0}`  // Vraćanje spremljenih izmena  

## GRANE
`git BRANCH develop` // stvara granu develop, koju cu kasnije moci da spojim sa master granom ili da je obrisem.  
`git BRANCH -v` // pregled svih grana  
`git BRANCH -d develop` // brisanje develop grane  
`git CHECKOUT develop` // prebacivanje na develop granu. Pre ovoga uraditi commit da bi snimio  
`git MERGE develop` // Prilikom spajanja grana, potrebno je vratiti se na roditeljsku granu (master) i pozvati komandu git merge \<develop>  
`git REBASE master` // Drugi nacin spajanja. Uglavno služi u svrhe dopunjavanja sporednih grana (develop) izmenama sa master grane. Ovo pokrecem dok sam na develop grani.  

## FAJL .gitignore  
U njega upisujem fajlove ili /foldere koji ce biti totalno ignosisani, kao da nepostoje.  
\# ovo je komentar  
log/ // ignoriši sve datoteke u log folderu  
*.txt // ignoriši sve tekstualne datoteke  
!users.txt // ali ne i datoteku 'users.  
css/**/*.css // ignoriši sve css datoteke bilo gde u css folderu  

### manje bitne stvari
video uputstvo: <https://www.youtube.com/watch?v=SWYqp7iY_Tc&ab_channel=TraversyMedia>  
`git`        // prikaz svih komandi  
`touch`	// stvaranje novog fajla  
`git --version`  // provera verzije  
`clear` 		// brisanje ekrana  



### Novi repozitorijum, github uptstva

Quick setup — if you’ve done this kind of thing before  
	
SSH: git@github.com:djlabat/George.git  
HTTPS: https://github.com/djlabat/George.git   


…or create a new repository on the command line  
echo "# George" >> README.md  
git init  
git add README.md  
git commit -m "first commit"  
git branch -M main  
git remote add origin https://github.com/djlabat/George.git  
git push -u origin main  
                
…or push an existing repository from the command line  
git remote add origin https://github.com/djlabat/George.git  
git branch -M main  
git push -u origin main  

…or import code from another repository  
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.  

### GIT PAGES
#### Pravljenje stranice
   * pratim proceduru sa GitHub Pages, napravio sam sajt
   * cloniram je na moj komp: git clone [https://...repozitorijem](#git-pages)
   * `code .`
   * napravim index.html > editujem ga
   * provera: ime mog branch-a: git status // main
   * `git add .`
   * `git commit -m 'initial commit'`
   * `git push origin main`
   * Provera: da li se Upload na GitHub

Bitna stvar: Kad napravim stranicu sa README.md i Index.html odem na → GitHub Pages: Settings → Sekcija: GitHub pages → Source: Main Branc → [ Save ]. Provera: trebalo bi da se na tom istom mestu ↑ u settings-u pojavi i adresa stranice


#### Editovanje sajta

```txt
        ┌── styling ──┐
main ═══╧═════════════╧═══ main
```
   * pravim novi branch: `git checkout -b styling`
   * Editujem sajt u VS CODE
   * `git add .`
   * `git commit -m styling`
   * upload Branch: `git push origin styling`
   * odem na gitHub (proverim upload), stvoren novi branch → Open pull request, Pull-ujem, Merge-ujem

#### Promena branch-a
```txt
        ┌── site ──╔══════
main ═══╧══════════╩──────
```


   * pravim novi branch: `git checkout -b site`
   * upload Branch: `git push origin site`
   * GitHub Settings → promenim branch na site

#### Tip & Tricks
   - editovanje sajta i na GitHub (commit + 10 sec + F5)

### ERRORS
   - Otvorim folder u VSCode i pop-up mi prozorcic (dole-desno) da ovaj folder nije bezbedan jer neki drugi user je vlasnik, nesto u tom smislu kenja. Samo klikni na dugme [Manage unsafe], pa gore u vrhu ekrana izaberi current folder.
   - Kada pravim projekat od kojeg cu posle napraviti sajt na GitHub, bitno je fajl nazvati `index.html` (mala slova) inace ce biti problema.

<style>
   h1, h2, h3, h4, h5, h6 {
      color: yellow
   }
</style>
