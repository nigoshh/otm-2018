# EI AJANTASALLA, lukeminen omalla vastuulla

# Viikon 1 tehtävät

Tehtävät on tarkoitus tehdä joko pajassa tai omatoimisesti. Tehtävien palautuksen deadline on ma 19.3. klo 23:59

Tehtävät palautetaan Githubin ja Labtoolin avulla. Lisää palautuksesta myöhemmin. Osa tehtävistä ei näy palautuksesta mitenkään. Niiden tekemättä jättäminen näkyy puuttuvana osaamisena ja saattaa aiheuttaa myöhemmin hankaluuksia.

Viikon palautuksista on tarjolla 2 pistettä. Pisteytys arvioidaan palautuksen laadun mukaan.

## Komentorivin harjoittelua

Graafisten käyttöliittymien olemassaolosta huolimatta ohjelmistoalalla on edelleen erittäin tärkeää hallita komentorivin eli terminaalin käyttö. 

## osa 1

Opettele käyttämään "riittävästi" komentoriviä (ks. alla oleva lista). Opettelu käy ehkä helpoiten tekemällä osoitteessa [https://www.codecademy.com/learn/learn-the-command-line](https://www.codecademy.com/learn/learn-the-command-line) olevan onlinekurssin kaksi ensimmäistä osaa _Navigating the File System_ ja _Viewing and Changing the File System_ (maksullisista pro-episodeista ei kannata välittää).

Tämän tehtävän jälkeen sinun tulisi hallita seuraavat asiat:
* käsitteet
  * root directory
  * home directory
  * parent directory
  * child directory
  * working directory
  * .. ja *
* ja osata käyttää komentoja
  * pwd
  * cd
  * ls, ls -a, ls -l, ls -t
  * mkdir
  * touch
  * cp
  * rm, rm -r
  * mv

Tulet tarvitsemaan komentorivin käyttötaitoja tällä kurssilla ja muutenkin opinnoissasi.

## osa 2

Aktivoi ns. cs-tunnuksesi [täällä](https://www.cs.helsinki.fi/passwd) jos et ole jo sitä aiemmin tehnyt.

Ota ssh-yhteys linuxpalvelimeen _melkki.cs.helsinki.fi_, _melkinpaasi.cs.helsinki.fi_ tai _melkinkari.cs.helsinki.fi_. Linuxilla ja macilla yhteys otetaan komentoriviltä komennolla _ssh kayttajatunnus@palvelimenosoite_. Windowsilla ssh-yhteyden ottaminen onnistuu esimerkiksi [putty:llä](http://www.putty.org).

Kirjauduttuasi laitoksen palvelimelle, tee seuraavat toimenpiteet:
* luo kotihakemistoosi hakemisto _kurssit_
* luo hakemistolle _kurssit_ alihakemisto _otm2018_
* ja luomallesi hakemistolle alihakemisto _viikko1_
* mene kotihakemistoosi ja luo sen alle hakemisto _temp_
* mene hakemistoon _temp_
* hae osoitteessa _https://raw.githubusercontent.com/mluukkai/otm-2018/master/misc/Unicafe.zip_ oleva tiedosto [wget](https://en.wikipedia.org/wiki/Wget)-ohjelmalla
  * wget toimii siten, että sille annetaan ladattava tiedosto parametriksi
* haettu tiedosto on _zip-paketti_, pura se _unzip_-ohjelmalla
  * myös unzip toimii siten, että sille annetaan purettava tiedosto parametriksi
* komennon suorittamisen jälkeen hakemistoon on ilmestynyt hakemisto _Unicafe_
* siirrä hakemisto hakemiston _kurssit/otm2018/viikko1_ alihakemistoksi
* poista zip-paketti
* poista hakemisto _temp_
* mene nyt uudessa paikassa olevaan hakemistoon _Unicafe_
* suorita komento _mvn clean_
  * jos näen rivien joukossa ilmoituksen _BUILD SUCCESS_ on tehtävä tehty

**Mene tämän jälkeen _kotihakemistoon_ ja anna komento _tree kurssit_. Copypastea komennon tulostus talteen, tarvitset sitä myöhemmin.**

## tab complete

Komentoriviä käyttäessä kannattaa ehdottomasti totutella _tab-completen_ käyttöön. _Tab_ on näppäin, joka näyttää suunnilleen seuraavalta

![](https://github.com/mluukkai/otm2016/raw/master/img/tab.jpg)

Tab:ia painamalla voit komentorivillä täydentää kirjoittamasi komennon nimen tai parametrin. Esim. jos olet siirtymässä hakemistoon nimeltään _ohjelmistotekniikan-menetelmat-kevat-2018_, riittää että kirjoitat <code>cd oh</code> ja painat tabia. Jos hakemistossasi ei ole muita tiedostoja tai hakemistoja, jotka alkavat merkeillä _oh_, nimi täydentyy. Jos on, niin voit joutua kirjoittamaan merkin tai kaksi lisää.

Myös komentojen nimet voi täydentää tab-completella. Esim. haluat avat _chromium-browser_ web-selaimen komentoriviltä, riittää että kirjoitat <code>chro</code> ja painat tabia. Komennon nimi täydentyy.

Ei pidä myöskään unohtaa _nuolta ylöspäin_. Sen avulla voit selata aiemmin kirjoittamiasi komentoja.

## yhtäaikaiset terminaalit / terminaalin tabit

Aloitteleva komentorivin käyttäjä pitää usein ainoastaan yhtä terminaali-ikkunaa kerrallaan auki. Useimmissa tilanteissa työtehosi moninkertaistuu, jos avaat useita terminaaleja näytöllä tai avaat yhteen terminaaliin useita "tabeja" eli välilehtiä. Uuden tabin saat avautumaan painamalla yhtä aikaa _ctrl_, _shift_ ja _t_ tai sovelluksen valikosta (joka laitoksen Linuxeissa sijaitsee ruudun yläreunassa).
  
## Versionhallinta

Tutustumme seuraavaksi versionhallintaan. 

Mitä tarkoitetaan versionhallinnalla? Lainaus sivulta [https://www.atlassian.com/git/tutorials](https://www.atlassian.com/git/tutorials)

> Version control systems are a category of software tools that help a software team manage changes to source code over time. Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.

Vaikka ylläoleva puhuu versionhallinnasta ohjelmistotiimien yhteydessä, kannattaa versionhallintaa käyttää oikeastaan yhdenkin hengen projekteissa ja muunkinlaisen materiaalin, kuin koodin hallinnoimiseen. Esim. tämän kurssin kaikki materiaali on talletettu versionhallintaan.

Nykyään suosituin versionhallintaohjelmisto on [git](https://git-scm.com). Tutustumme tänään gitin alkeisiin. 

**HUOM** tämä tehtävä tulee tehdä Linuxilla tai Macilla, jolle on asennettu Git. Helpointa lienee tehdä tehtävä laitoksen koneella. Git kannattaa joka tapauksessa asentaa omalle koneelle. Gitin voi asentaa myös Windowsille.

## Gitin alkeet

### konfiguraatioita

Avaa terminaali. 

Määrittele gitille oma nimesi sekä käyttämäsi email-osoite antamalla komennot:

```
 git config --global user.name "Your Name"
 git config --global user.email you@example.com
```

Varmista komennolla <code>git config -l</code>, että määrittelyt menivät oikein.

Määritellään vielä git käyttämään sopivia värejä komennolla <code>git config --global color.ui</code> ja **vaihdetaan gitin käyttämäksi oletuseditoriksi** _nano_ komennolla <code>git config --global core.editor nano</code>
* jos käytät vimiä, voit jättää oletuseditorin muuttamatta

### repositorio

Tee nyt sopiva hakemisto gitin harjoittelua varten ja mene hakemistoon, eli anna esim. komennot:
* mkdir otm_viikko3
* cd otm_viikko3

**HUOM:** varmista nyt että olet luomassasi hakemistossa, eli jos suoritat komennon _ls_, ei hakemistossa pitäisi olla mitään.

Luodaan hakemistosta paikallinen _git-repositorio_ antamalla komento <code>git init</code>

Git ilmoittaa alustaneensa repositorion:

<pre>
mluukkai@melkinpaasi:~/otm_viikko3$ git init
Initialised empty Git repository in /home/ad/fshome4/u4/m/mluukkai/Linux/otm_viikko3/.git/
</pre>

Jos katsot hakemiston sisältöä komennolla <code>ls -la</code> huomaat, että hakemiston sisälle on ilmestynyt hakemisto <code>.git</code>. Git käyttää luotua hakemistoa pitääkseen kirjaa repositorioon talletetuista tiedostoista.

**HUOM** koska hakemiston nimi (_.git_) alkaa pisteellä, ei komento _ls_ näytä sitä oletusarvoisesti. Parametri _a_ näyttää myös pisteellä alkavat tiedostot ja hakemistot. Kokeile, miten _ls -a_ ja _ls -la_ eroavat toisistaan!

Pysy edelleen repositorion sisältävässä hakemistossasi _ otm_viikko3_.

Luo hakemistoon tiedosto nimeltään _tiedosto.txt_, esim. komennolla <code>touch</code>. Luotuasi tiedoston, suorita komento <code>git status</code>:

<pre>
mluukkai@melkinpaasi:~/otm_viikko3$ touch tiedosto.txt
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	tiedosto.txt

nothing added to commit but untracked files present (use "git add" to track)
mluukkai@melkinpaasi:~/otm_viikko3$
</pre>

Git ilmoittaa, että on olemassa tiedosto, joka on tilassa _untracked_, eli tiedostoa ei ole lisätty versionhallinnan pariin.

Kuten komennon tuloste kertoo, tiedoston lisääminen gitin alaisuuteen (...to include in what will be committed) tapahtuu komennolla <code>git add tiedosto.txt</code>

Suorita lisäys ja sen jälkeen komento <code>git status</code>:

<pre>
mluukkai@melkinpaasi:~/otm_viikko3$ git add tiedosto.txt
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   tiedosto.txt
</pre>

Git kertoo nyt, että _tiedosto.txt_ on niiden muutosten joukossa, jotka voidaan _commitoida_.

### commit

Commitoimisella tarkoitetaan tiedostojen ja hakemistojen sekä niihin liittyvien muutosten tallentamista _git-repositorioon_.

Suoritetaan commitointi antamalla komento <code>git commit -m"tiedosto.txt luotu"</code>

<pre>
mluukkai@melkinpaasi:~/otm_viikko3$ git commit -m"tiedosto.txt luotu"
[master (root-commit) 0e12cfa] tiedosto.txt luotu
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 tiedosto.txt
</pre>

Suorita jälleen komento <code>git status</code>

<pre>
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master
nothing to commit, working directory clean
</pre>

Git ilmoittaa, että _working directory clean_, eli hakemistosi on samassa tilassa kuin git-repositorio.

### working directory, index/staging,  repository  

**Muista käyttää tab-completea tehtäviä tehdessäsi!**

Kun teet muutoksia hakemistosi alla oleviin tiedostoihin (tai hakemistoihin), kohdistuvat muutokset _working directoryyn_ eli työhakemistoon. 
* Tee jokin muutos tiedostoon tiedosto.txt 
  * käytä tiedostojen editointiin _nano_-editoria. Editori käynnistyy komentoriviltä komennolla _nano tiedosto.txt_
  * saat tallennettua nanossa tiedoston painamalla yhtä aikaa _ctrl_ ja _o_
  * editori sulkeutuu painamalla _ctrl_ ja _x_
* Luo hakemistoon uusi tiedosto, nimeltään _toinen.txt_

Suorita jälleen <code>git status</code>

<pre>
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   tiedosto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	toinen.txt

no changes added to commit (use "git add" and/or "git commit -a")
</pre>

Git ilmoittaa nyt, että uusi tiedosto on _untracked_ ja että aiemmassa tiedostossa on muutoksia, jotka eivät ole _staged for commit_.

Toimitaan ohjeen mukaan eli lisätään muutokset ja uusi tiedosto commitoitavien joukkoon. Molempien tiedostojen yhtäaikainen "addaaminen" onnistuu komennolla <code>git add .</code>

Tarkistetaan taas tilanne koennolla <code>git status</code>

<code>
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   tiedosto.txt
	new file:   toinen.txt
</code>

Sekä muutos että uusi tiedosto ovat nyt valmiina committoitavaksi. 

Committointi onnistuu komennolla _git commit_. Kuten edelliselläkin kerralla, annetaan komennolle parametrina _commit-viesti_, eli merkkijono, joka kuvaa mitä muutoksia uusi commit tuo edelliseen nähden:

<code>git commit -m"muutos ja lisäys"</code>

Tarkasta committoinnin jälkeen jälleen tilanne komennolla _git status_.

**HUOM** jos suoritat commitoinnin vahingossa ilman commit-viestiä, eli parametria _-m_, avaa git tekstieditorin ja olettaa että haluat kirjoittaa commit-viestin editoriin.

Tiedostot ja niihin tehdyt muutokset voivat siis olla gitin suhteen _kolmessa eri tilassa_. 
* Aluksi tiedostot (tai niihin tehdyt muutokset) ovat vain _working directoryssä_ ja git ei noteeraa niitä ennen kun ne lisätään komennolla <code>git add</code>. 
* Tämän jälkeen tiedostot ovat valmiina commitoitavaksi. Gitin terminologian mukaan valmiina committoitavaksi olevat tiedostot ovat _staging_-alueella.
*  Komento <code>git commit</code> siirtää stagingissa olevat muutokset repositorioon eli luo uuden _commitin_. 

Seuraava kuva havainnollistaa sitä, miten tiedoston _tila_ vaihtuu git-komentoja tekemällä.

![](https://github.com/mluukkai/otm2016/raw/master/img/lh3-2.png)

Kun tiedosto luodaan, menee se gitin _working directoryyn_. Komennolla _git add_ tiedosto siirtyy _staging_ -alueelle, eli valmiiksi committointia varten. Stagingissa oleva tiedosto viedään (eli "commitoidaan") repositorioon komennolla _git commit_. Kun committoitua tiedostoa taas editoidaan, menevät muutokset jälleen _working directoryyn_.

## git commit

Jokainen komennon _git commit_ suorittaminen siis synnyttää repositorioon uuden commitin, eli uuden "tilan". Komennolla <code>git log</code> on mahdollista nähdä, mitä committeja repositorio sisältää:

<pre>
mluukkai@melkinpaasi:~/otm_viikko3$ git log
commit 50c786fdc41104cdfe3e60845df40820feb33d40
Author: Matti Luukkainen <mluukkai@iki.fi>
Date:   Mon Nov 7 18:18:19 2016 +0200

    lisäys ja muutos

commit 0e12cfa5de9186eb948ac446c6b3f240ff11189d
Author: Luukkainen Matti <mluukkai@melkinpaasi.cs.helsinki.fi>
Date:   Mon Nov 7 16:11:33 2016 +0200

    tiedosto.txt luotu
mluukkai@melkinpaasi:~/otm_viikko3$
</pre>

Gitin logi kertoo jokaisen commitin ajan tekijän, viestin ja _tunnisteen_. Tunnisteita käytetään, jos on esim. tarvetta palata johonkin vanhan commitin tilaan. 


Voit selata logia nuolinäppäimillä. Pääset ulos _git log_:ista painamalla _q_.

## lisää harjoittelua

Muista käyttää komentoa _git status_ mahdollisimman usein!
* älä myöskään unohda tab-completea

* Luo tiedosto _kolmas.txt_
* Lisää se commitoitavaksi ja commitoi 
* Muuta tiedostojen _toinen.txt_ ja _kolmas.txt_ sisältöä ja commitoi muutokset
* Luo hakemisto _stuff_ ja sen sisälle jokin tiedosto
* Lisää muutokset committoitavaksi ja committoi 
  * Huomaa, että hakemiston lisääminen riittää, sen sisältämät tiedostot tulevat automaattisesti lisätyksi
* Katso miltä git logi näyttää

## gitk

Giting committeja voi tarkastella myös graafisella _gitk_-komennolla (OSx:lle vastaava työkalu on [gitx](http://gitx.frim.nl)). Suorita komento repositoriossa:

![](https://github.com/mluukkai/otm2016/raw/master/img/lh3-1.png)

Vasemmalla yläkulmassa näet kaikki commitit. Uusin tilanne ylimpänä. Uusimman commitin nimi on *master*. Klikkaamalla commitia näet muissa ikkunoissa commitiin liittyviä tietoja. Oikealla alakulmassa näet ne tiedostot, jotka ovat muuttuneet commitissa (jos valinta on _patch_) tai ne tiedostot, joita repositoriossa oli olemassa commitin aikana (jos valinta on _tree_). Vasemmassa alakulmassa pystyt tarkastelemaan commitin tiedostoihin tekemiä muutoksia tai tiedostojen tilaa commitin aikana.  Valinnat ovat hieman hämäävät sillä ne toimivat eri tavoin riippuen oikean puolen moodista.

Seuraavaa tehtävää tekiessäsi kannattaa terminaaliin avata uusi välilehti, jotta voit pitää gitk:ta käynnissä.

* Kopioi tiedostoon _tiedosto.txt_ jostain paljon tekstiä ja commitoi tiedosto
* Poista nyt osa tiedoston tekstistä ja lisää tiedostoon hieman lisää tekstiä
* commitoi muutosten jälkeen
* Päivitä gitk:n näkymä (file/update) ja katso miten muutokset näkyvät (tarkastele kahta ylintä committia) 
  * valitse oikeasta alakulmasta _patch_ ja vasemmasta _diff_
  * näin näet commitin aiheuttamat muutokset [diff](https://fi.wikipedia.org/wiki/Diff)-muodossa
  * jos oikealta on valittuna _tree_ näkyy vasemmalla puolella (valinnasta riippumatta) tiedostojen commitin aikainen tilanne 

## tiedoston poistaminen ja uudelleennimentä

* Poista tiedosto _toinen.txt_
* suorita _git status_
* commitoi muutos
  * poista ensin tiedosto gitin alaisuudesta komennolla _git rm_
* varmista komennolla _git status_ että kaikki on niinkuin kuuluukin
* muuta tiedoston _tiedosto.txt_ nimeksi _eka.txt_
  * uudelleennimentä tapahtuu komennolla _mv_
* suorita _git status_
  * miten git käsittelee uudelleennimennän?
* commitoi muutos

## git add -p

* Tee jotain muutoksia tiedostoihin _eka.txt_ ja _kolmas.txt_
  * tee sekä lisäyksiä että poistoja
* lisää ne commitoitavaksi komennolla _git add -p_
  * git näyttää nyt jokaisen tekemäsi muutoksen _patch_-muodossa ja pyytää varmistamaan lisätäänkö muutos commitoivaksi
  * hyväksy painamalla _y_ ja enter
* commitoi muutokset
* tee tiedostoihin tehtyjen muutosten commitoitavaksi lisääminen *aina* komennolla _git add -p_, näin pääset tarkastamaan, että muutokset ovat juuri ne mitä oletat olevasi lisäämässä
* Huomaa, että kokonaan uudet tiedostot eivät siirry committoitavaksi komennolla _git add -p_ 

## muutosten peruminen

Joskus tiedostoihin tulee tehtyä muutoksia, jotka on tarpeen perua 
* tee nyt joku muutos tiedostoon _eka.txt_, **älä** lisää tiedostoa committoitavaksi
* suorita komento *git status*

```bash
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   eka.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Kuten oletettua, git kertoo että olemme tehneet muutoksia jotka eivät ole "staged for commit", eli lisättyjä commitoitavaksi. 
* Päätetäänkin perua muutokset. Se onnistuu komennolla <code>git checkout -- eka.txt</code>
* Kun suoritat uudelleen komennon _git status_ huomaat, että working directory ei enää sisällä muutoksia:

```bash
mluukkai@melkinpaasi:~/otm_viikko3$ git checkout -- eka.txt
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master
nothing to commit, working directory clean
```

* Varmista vielä, että tiedoston sisältö on sama kuin ennen muutoksia

Myös stagingiin viety eli valmiina committoitavaksi oleva muutos voidaan perua. 
* Tee muutoksia tiedostoon _kolmas.txt_ ja lisää se committoitavaksi. **Älä** kuitenkaan committoi. 
* git statuksen pitäisi näyttää seuraavalta

``` bash
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   kolmas.txt

mluukkai@melkinpaasi:~/otm_viikko3$
```

Ohje muutoksen perumiseen löytyy git statuksen tulosteesta.
* suorita muutokset peruva komento <code>git reset HEAD kolmas.txt</code>
* katsotaan jälleen _git status_

``` pre
mluukkai@melkinpaasi:~/otm_viikko3$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   kolmas.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Tiedosto ei siis enää ole _staged_-tilassa, muutokset ovat kuitenkin _working directoryssä_, eli jos katsot tiedoston sisällön, muutokset ovat vielä olemassa
* pääset perumaan muutokset kokonaan antamalla komennon <code>git checkout -- kolmas.txt</code>
* varmista, että tiedosto on palannut muutoksia edeltävään tilaan

Seuraavassa tiedoston tilaa kuvaava kaavio täydennettynä, eli jos tiedosto on lisätty committoitavaksi, eli se on  _staged_, voidaan muutos perua komennolla _git reset HEAD_. Tällöin muutokset kuitenkin vielä jäävät tiedostoon, eli ovat _working directoryssä. Tiedosto saadaan palautettua repositoriossa olevaan edellisen commitin tilaan komennolla _git checkout_.

![](https://github.com/mluukkai/otm2016/raw/master/img/lh3-3.png)

## harjoittelua

* luo hakemisto _tiedostoja_ ja hakemiston sisälle tiedostot _file1_, _file2_ ja _file3_
* commitoi muutokset
  * muista miten pystyt lisäämään kokonaisen hakemiston sisällön committoitavaksi yhdellä komennolla
* muuta tiedoston _file1_ sisältöä ja poista tiedosto _file2_
* peru muutokset!
* muuta tiedoston _file3_ sisältöä, lisää commitoitavaksi
* peru muutokset!
* poista tiedosto _file1_ ja uudelleennimeä tiedosto _file2_ tiedostoksi _file22_
* committoi 

## .gitignore

On tilanteita, joissa emme halua tiedostojen menevän versionhallinnan alaisuuteen. maven-projektien hakemisto _target_, joka sisältää [maven-komentojen aikaansaannokset](https://github.com/mluukkai/OTM2016/wiki/Viikon-2-paikanpaalla-tehtavat#3-maven-projektin-hakemistorakenne), on tyypillisesti hakemisto, jota emme halua versionhallinnan pariin.

Git-repositorion juureen sijoitettavassa [.gitignore](https://www.atlassian.com/git/tutorials/gitignore)-tiedostossa voidaan määritellä, mitä tiedostoja ja hakemistoja git jättää huomioimatta eli _ignoroi_

* Muuta viime viikon paikanpäällä tehtävässä tekemäsi hakemisto _Unicafe_ git-repositorioksi
  * komento _git init_
  * **HUOM:** älä vielä lisää mitään commitoitavaksi!
  * muista tässäkin myös komennon _git status_ aktiivinen käyttö!
* Luodaan repositorion juureen tiedosto _.gitignore_ ja määritellään siihen ignoroitavaksi hakemisto _target_ ja tiedosto _nbactions.xml_, eli
  * luo tiedosto nanolla
  * tiedoston sisällöksi tulee

<pre>
target
nbactions.xml
</pre>

* kun nyt teet komennon _git status_ pitäisi tuloksen olla seuraava:

<pre>
mluukkai@melkki:~/Unicafe$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	pom.xml
	src/
</pre>

* eli vaikka hakemistossa on tiedosto _nbactions.xml_ sekä alihakemisto _target_, ei git niitä huomioi
* lisää hakemiston sisältö repositorioon
* commitoi 
* tarkasta tilanne komennolla _git status_
* kokeile nyt suorittaa maven-komentoja, jotka tekevät muutoksia hakemistoon _target_
  * esim. testien suoritus ja testiraportin generointi
* tarkasta komennolla _git status_, että git ei välitä muutoksista
* tee jokin muutos projektin koodiin ja tarkasta että git huomaa tilanteen
* commitoi muutokset

## kertausta

* Tee uusi hakemisto
* Tee hakemistosta git-repositorio
  * muista koko ajan käyttää tärkeää komentoa _git status_
  * muista myös _git add -p_ muutoksia lisätessäsi
* Lisää hakemistoon tiedosto nimeltään README.md
* Kirjoita tiedostoon jotain
  * käytä nano-editoria
  * muotoile tekstisi [markdown-notaatiota](https://guides.github.com/features/mastering-markdown/) käyttäen, tee tiedostoon esim. jokin otsikko, tavallista tekstiä, joka sisältää tummennettuja ja vinonnettuja osuuksia
  * näemme pian tekstin ruudulla muotoiltuna
* commitoi tiedosto
  * muista aina commitoinnin yhteydessä _lisätä_ tiedosto/muutokset commitoitavaksi

## Github 

Gitin käytöstä on toki hyötyä jo harjoittelemallammekin tavalla, eli muodostamalla paikallisen koneen hakemistosta repositorio. Pääsemme kuitenkin nauttimaan kertaluokkaa suuremmista hyödyistä liittämällä repositoriomme internetissä olevaan _etärepositorioon_. Etärepositorion kautta repositorion tiedostot on helppo jakaa useiden koneiden tai/ja useiden käyttäjien kesken.

Internetin johtava paikka etärepositorioiden tallettamiseen on [GitHub](https://github.com)

* Luo itsellesi tunnus GitHubiin 
* Luo uusi repositorio
  * uuden repositorion luomistoiminto löytyy vasemman ylänurkan plus-symboolin alta
* **Älä laita rastia** kohtaan *Initialize this repository with a README*

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-2.png" alt="alt text" width="600">

Seuraavaksi haluamme liittää GitHubiin luodun repositorion paikallisen koneen repositorin etärepositorioksi.
* etärepositorion lisääminen onnistuu komennolla _git remote add_
* varmista, että kohdasta "Quick setup..." on valittu **SSH**

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-7.png" alt="alt text" width="600">

* kopioi GitHubiin avautuneesta näkymästä ylempi rivi kohdasta *...or push an existing repository from the command line*
* omassa esimerkissäni rivi on

``` bash 
git remote add origin git@github.com:mluukkai-cs/otm2016-git-viikko5.git
```

* pastea rivi komentoriville ja suorita komento painamalla enter
* suorita komento _git remote -v_
* tulostus kertoo, että githubin etärepositorio on liitetty paikalliseen repositorioosi nimellä _origin_

``` bash
mluukkai@melkki:~/otm_viikko5$ git remote  -v
origin	git@github.com:mluukkai-cs/otm2016-git-viikko5.git (fetch)
origin	git@github.com:mluukkai-cs/otm2016-git-viikko5.git (push)
```

* _origin_ on etärepositorion oletusarvoinen nimi. Nimi voi olla mikä tahansa ja etärepositorioitakin voi olla useita

* voimme siirtää repositoriomme tilan etärepositorioon komennolla _git push_
* kokeillaan

```
mluukkai@melkki:~/otm_viikko5$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master
```

Tulee pieni valitus ja git ehdottaa komennon parametrillista versiota. Kokeillaan sitä:

```
mluukkai@melkki:~/otm_viikko5$ git push --set-upstream origin master
Warning: Permanently added the RSA host key for IP address '192.30.253.112' to the list of known hosts.
Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

## julkinen avain

Jos olet jo asettanut julkisen avaimen esim. Tietokantojen perusteissa, pushauksen pitäisi toimia ja voit siirtyä [seuraavaan kohtaan](https://github.com/mluukkai/OTM2016/wiki/Viikon-5-paikanpaalla-tehtavat#tiedostot-githubissa).

Pushaus ei edelleenkään toimi. Nyt kyse on siitä, että git haluaisi suorittaa [julkisen avaimen](https://the.earth.li/~sgtatham/putty/0.55/htmldoc/Chapter8.html) autentikoinnin. Se ei kuitenkaan onnistu koska emme ole kertoneet gitille julkista salausavaintamme.

* luo salausavain antamalla komentoriviltä komento _ssh-keygen_
  * voit vastata kaikkiin kysymyksiin enterillä
* syntyy kaksi salausavainta, salainen ja julkinen. Ne sijoitetaan kotihakemistosi alla olevaan hakemistoon _.ssh_
* mene hakemistoon ja katso hakemiston sisältöä
* tiedosto _id_rsa.pub_ sisältää julkisen avaimen, se on tarkoitus kopioida githubiin, jotta avaimeen perustuva kirjautuminen onnistuisi
* näet tiedoston sisällön komennolla _cat id_rsa.pub_

* mene GitHubin asetussivulle klikkaamalla oikean yläkulman symbolista ja valitsemalla _settings_
* valitse settingseistä _SSH and GPG keys_
* luo uusi _SSH-avain_ 
  * anna avaimelle joku _title_ (esim. laitos) ja kopioi tiedoston id_rsa.pub sisältö kohtaan _key_

* Suorita uudelleen push:

```
mluukkai@melkki:~/otm_viikko5$ git push --set-upstream origin master
Counting objects: 8, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (8/8), 714 bytes | 0 bytes/s, done.
Total 8 (delta 0), reused 0 (delta 0)
To git@github.com:mluukkai-cs/otm2016-viikko5.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
``` 

* nyt kaikki näyttää toimivan

## Tiedostot GitHubissa

* mene GitHub-repositoriosi sivulle
  * löydät kaikki repositoriosi valitsemalla GitHubin oikeasta yläkulmasta klikkaamalla "your profile" ja avautuvasta näkymästä "repositories"
* huomaat että tiedostot näkyvät nyt repositorion sivulla. Sivulle renderöityy repositorion juuressa olevan README.md:n sisältö markdown-muotoiltuna

* voit editoida repositoriossa olevia tiedostoja suoraan githubin editorilla menemällä tiedoston sivulle ja painamalla kynäsymbolia
* tee README.md:hen linkki käyttöohjeeseen, eli repositoriossa olevan hakemiston _dokumentointi_ sisältämään tiedostoon _kaytto-ohje.md_
  * ohje linkin muodostamiseen löytyy [täältä](https://guides.github.com/features/mastering-markdown/)
  * käyttöohjeen urlin saat navigoimalla GitHubissa tiedostoon ja kopioimalla osoitteen selaimen osoiteriviltä 
* jos teet kaiken oikein, pääset README.md:ssä olevaa luomaasi linkkiä klikkaamalla käyttöohjeeseen

* GitHubissa tekemämme muutokset ovat tehneet etärepositorioon uuden commitin
* etärepositorio on nyt _edellä_ paikallista repositorioamme
* saamme tuotua muutokset paikalliselle koneelle komennolla _git pull_
* kokeile komentoa ja varmista, että muuttunut sisältö on nyt paikallisessa repositoriossa


## lisää githubia

* Tee paikallisella koneella jokin muutos esim. tiedostoon README.md
* lisää ja committaa muutos
* vie muutokset githubiin komennolla _git push_
* varmista GitHubista että muutokset näkyvät

* Paikallinen repositoriosi ja GitHubin etärepositorio ovat jälleen samassa tilassa 
* Lisää GitHubin avulla hakemistoon _dokumentaatio_ uusi tiedosto, nimeltään *maarittelydokumentti.md*
  * piirrä [yuml.me](http://yuml.me):lla jokin kaavio (valmiit esimerkkikaaviot käyvät)
  * lisää kaavio kuvaksi määrittelydokumenttiin
* Tee README.md:sta linkki uuteen tiedostoon
* pullaa muutokset paikalliselle koneelle

## paikallisen ja etärepositorion epäsynkrooni

* joskus käy niin, että paikallinen ja etärepositorio menevät epäsynkroniin, siten että molempiin tehdään yhtäaikaa uusi commit
* luodaan tälläinen tilanne
* tee paikalliseen repositorioon muutos tiedostoon _README.md_, lisää ja committoi muutos
  * **älä** pushaa muutosta GitHubiin
* tee GitHubiin muutos johonkin muualle, esim. tiedostoon _kaytto-ohje.md_
  * editoi siis tiedostoa suoraan GitHubissa
* yritä nyt pushata paikallisen repositorion muutokset githubiin
* seurauksena on virheilmoitus

``` 
mluukkai@melkki:~/otm_viikko5$ git push
To git@github.com:mluukkai-cs/otm2016-viikko5.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:mluukkai-cs/otm2016-viikko5.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
mluukkai@melkki:~/otm_viikko5$
``` 

* Tulet törmäämään tähän varmaan useasti jatkossakin
* Ongelma ei ole paha. Koska paikalliset ja GitHubin muutokset ovat kohdistuneet eri tiedostoihin selviämme helposti 
* ensin pullaamme muutokset paikalliseen repositorioon komennolla _git pull_
  * pullaaminen synnyttää ns. merge commitin jolle joudumme määrittelemään commit-viestin avautuvaan editoriin
  * oletusarvoinen viesti käy, eli riittää että poistut editorista tallentaen muutokset
* ja pushaamme ne uudelleen githubiin
* nyt paikallinen ja etärepositorio ovat taas synkroonissa
* katso repositorion tilaa nyt komennolla _gitk_
* näet, että repositorion uusimmalla commitilla on nyt kaksi edeltäjää, paikallinen commit ja etärepositorion commit

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-3.png" alt="alt text" width="800">

Jos muutokset olisivat kohdistuneet samaan tiedostoon, olisi syntynyt hieman vakavampi tilanne, eli _merge-konflikti_. Konfliktit on pakko selvittää itse editorin avulla. On toki olemassa työkaluja, mergetooleja, jotka auttavat konfliktin selvittämisessä. Emme kuitenkaan mene tällä kurssilla merge-konflikteihin.

Nyrkkisääntönä kannattaa pitää aina sitä, että kun rupeat työskentelemään paikallisessa repositoriossa, pullaa ensin kaikki muutokset etärepositoriosta. Ja kun lopetat työskentelyn, pushaa muutokset etärepositorioon. Näin konflikteja ei yhden ihmisen työskentelyssä todennäköisesti tule.

## GitHubissa olevan repositorion kloonaaminen

Teimme äsken repositorion ensin paikallisesti ja linkitimme sen GitHubissa olevaan etärepositorioon. Usein tilanne on sellainen, missä haluaisimme GitHubissa jo olevan repositorion omalle koneellemme. Tähän on tarkoitettu gitin komento clone.

* Luo GitHubiin uusi repositorio, laita tällä kertaa rasti kohtaan "Initialize this repository with a README"
* GitHub luo repositorion sisälle README.md:n
* Lisää githubista repositorioon uusi tiedosto ja tee jotain muutoksia README.md:hen
* klikkaa kohtaa _clone or download_ ja kopioi kloonaus-url
  * varmista että valittuna on "clone with SSH"

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-4.png" alt="alt text" width="400">

* mene sopivaan hakemistoon paikallisella koneella
  * **ÄLÄ** kuitenkaan mene minkään git-repositorion sisälle
* anna kloonauskomento, parametrina kloonaus-url

``` 
mluukkai@melkinkari:~$ git clone git@github.com:mluukkai-cs/otm2016-uusi.git
Cloning into 'otm2016-uusi'...
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 9 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Checking connectivity... done.
mluukkai@melkinkari:~$
``` 

Hakemistoosi syntyy uusi hakemisto, esimerkissä nimeltään _otm2016-uusi_, eli oletusarvoisesti nimi päätellään kloonaus-urlista. Uuden hakemiston nimen voi myös määritellä itse antamalla komennolle lisäparametrin:

``` 
git clone git@github.com:mluukkai-cs/otm2016-uusi.git hakemiston_nimi
``` 

Syntynyt hakemisto on nyt git-repositorio, jonka sisältö on sama kuin etärepositoriossa.
* tee repositorioon jokin muutos, lisää ja committoi
* push muutokset githubiin
* varmista GitHubista että muutos menee perille

## hieman lisää mavenia

* Luo NetBeansilla maven-muotoinen projekti, jonka sijoitat tehtävien alussa tekemäsi _repositoriosi juureen_
  * projektin sijainnin pystyt määrittelemään uuden projektin luomisdialogin kohdassa _project location_
* Jos loit sovelluksen oikeaan paikkaan _git status_ -komennon tuloste on suunilleen seuraavanlainen

``` 
mluukkai@melkki:~/otm_viikko5$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	otmtestiappi/

nothing added to commit but untracked files present (use "git add" to track)
``` 

* lisää ja commitoi sovellus repositorioon
* tee sovellukselle yksinkertainen pääohjelma, eli luokka jonka sisällä on metodi

``` java
    public static void main(String[] args) {
        System.out.println("testing...");
    }
``` 

* **ÄLÄ** vielä suorita ohjelmaa
* lisää ja commitoi sovellus repositorioon
* kuten muistamme, maven-projektien alle syntyy komentojen suorittamisen seurauksena hakemisto _target_
* emme halua hakemistoa git-repositorioomme, eli se tulee ignoroida
* suorita nyt ohjelma
* huomaat että sovelluksen alle muodostuu hakemisto _target_
* jos kokeilet mitä _git status_ sanoo, huomaat että yllättäen git ignoroi syntyneen target-hakemiston
* NetBeans onkin lisännyt automaattisesti hakemiston ignoroitavaksi
* Katso miltä .gitignore näyttää, lisää ja commitoi siihen tullut muutos

Haluamme suorittaa ohjelmamme komentoriviltä ja laittaa ohjelmamme julkisesti saataville, siten että kuka tahasa pystyy käyttämään ohjelmaa. Tämä onnistuu helposti jos paketoimme ohjelmamme [jar-paketiksi](https://en.wikipedia.org/wiki/JAR_(file_format))

Jar-tiedosto on helppo luoda mavenilla. Tarvitsemme hieman konfigurointia.
* Lisää seuraava tiedoston pom.xml sisälle, esim. juuri ennen viimeistä riviä.
  * tiedostoa kannattaa editoida NetBeansilla


```xml
    <build> 
       <plugins>
           <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-shade-plugin</artifactId>
                <version>1.6</version>
                <executions>
                    <execution>
                        <phase>package</phase>
                        <goals>
                            <goal>shade</goal>
                        </goals>
                        <configuration>
                            <transformers>
                                <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                                    <mainClass>fi.helsinki.cs.otmtestiappi.Main</mainClass>
                                </transformer>
                            </transformers>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>        
``` 

Huomaa, että kohdan _mainClass_ on oltava **täsmälleen sama** kuin pääohjelman sisältävän luokan täydellinen nimi:

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-5.png" alt="alt text" width="800">

* Saat nyt luotua jar-tiedoston antamalla komentoriviltä komennon _mvn package_
* komento luo hakemiston _target_ sisälle kaksi jar-päätteistä tiedostoa, niistä oikea on se, jonka nimessä *ei* ole sanaa original
* ohjelman voi nyt suorittaa komennolla <code>java -jar jartiedoston_nimi.jar</code>
* suorita ohjelma komentoriviltä

## Github release

Jar-tiedosto siis generoituu hakemistoon target, eli se ei tallennu repositorioon. Miten saamme levitettyä ohjelmistomme potentiaalisille käyttäjille? 

Yksi mahdollisuus on luoda GitHubiin release, eli julkaistu versio.
* klikkaa repositorion GitHub-sivulta kohtaa "0 releases"
* määrittele julkaisun tiedot ja lisää jar-tiedosto klikkaamalla kohtaa "Attach binaries..."
  * jar-tiedosto kannattaa ehkä uudelleennimetä, mavenin generoima tiedostonimi on hieman ikävä

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-6.png" alt="alt text" width="800">

Nyt koodi on kenen tahansa ladattavissa menemällä GitHub-repositorioosi ja klikkaamalla repositoriosivusi kohtaa "1 release" ja suoritettavissa komennolla <code>java -jar tiedostonnimi.jar</code> olettaen, että koneelle on asennettu Javan versio 1.8

Tämän kurssin osalta git-harjoittelumme loppuu tähän. Nyt opittu riittää hyvin yhden ihmisen käyttöön, esim. ohjelmoinnin harjoitustyön yhteydessä.

Gitissä on runsaasti hyödyllisiä ominaisuuksia joihin emme vielä tutustuneet. 

## lisää gitiä

Gitin opiskelua kannattaa ilman muuta jatkaa myös omin päin. Internetistä löytyy suuri määrä enemmän tai vähemmän hyviä tutoriaaleja. Seuraavassa muutama linkki
* <https://www.atlassian.com/git/tutorials/>
* <http://learngitbranching.js.org>
* <http://ohshitgit.com>
* valmiita gitignoremäärittelyjä erityyppisille projekteille <https://github.com/github/gitignore>
