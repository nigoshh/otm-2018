# Esimerkkejä aiheista

### Hyvän aiheen ominaisuudet

* **Itseäsi kiinnostava aihe**
  * Innostava aihe auttaa huonoinakin hetkinä

* "Riittävän laaja"
  * Vältä eeppisiä aiheita, aloita riittävän pienestä. Yksi periodi on yllättävän lyhyt aika
  * Valitse kuitenkin aihe, jota saa laajennettua sopivasti
  * Hyvässä aiheessa on muutamia logiikkaluokkia, tiedostonkäsittelyä ja logiikasta eriytetty käyttöliittymä

* Kurssilla pääpaino on Ohjelmoinnin Perusteissa ja Jatkokurssilla opitussa asioissa
  * Käytettävyys
  * Toimivuus ja varautuminen virhetilanteisiin
  * Luokkien vastuut
  * Ohjelman selkeä rakenne
  * Laajennettavuus ja ylläpidettävyys

* **Tällä kurssilla ei ole tärkeää:**
  * Tekoäly
  * Grafiikka
  * Tietoturva
  * Tehokkuus
  
* **HUOMIO!** Kannattaa yrittää välttää aiheita, joissa pääpaino on tiedon säilömisessä tai käyttöliittymässä. Paljon tietoa säilövät sovellukset ovat vaikeita testata tämän kurssin esitietovaatimusten puitteissa, ja ne sopivat yleensä paremmin Tietokantasovellus-kurssille. Käyttöliittymäkeskeisissä aiheissa (esim. tekstieditori) voi olla vaikea keksiä sovelluslogiikkaa, joka on enemmän tämän kurssin painopiste (myös siksi koska käyttöliittymää ei tällä kurssilla testata ja testaus on kurssin keskeinen aihe - jos ei ole sovelluslogiikkaa, on vaikea myös kirjoittaa sille testejä)

### Esimerkkejä aiheista

Oman aiheen ei ole pakko olla allaolevasta listasta. Listassa on kuitenkin erilaisia esimerkkejä, joista voi toteuttaa oman versionsa.

* Hyötyohjelmat
  * Aritmetiikan harjoittelua
  * Tehtävägeneraattori, joka antaa käyttäjälle tehtävän sekä mallivastauksen (esim. matematiikkaa, fysiikkaa, kemiaa, ...)
  * Opintojen seurantajärjestelmä
  * IRC- tai Slack-botti
  * Code Snippet Manageri
  * Laskin, funktiolaskin, graafinen laskin
  * Budjetointi-sovellus
  * HTML WYSIWYG-editor (What you see is what you get)

* Reaaliaikaiset pelit
  * Tetris
  * Pong
  * Pacman
  * Tower Defence
  * Asteroids
  * Space Invaders
  * Yksinkertainen tasohyppypeli, esimerkiksi The Impossible Game

* Vuoropohjaiset pelit
  * Tammi
  * Yatzy
  * Miinaharava
  * Laivanupotus
  * Yksinkertainen roolipeli tai luolastoseikkailu
  * Sudoku
  * Muistipeli
  * Ristinolla (mielivaltaisen kokoisella ruudukolla?)

* Korttipelit
  * En Garde
  * Pasianssi
  * UNO
  * Texas Hold'em

* Omaan tieteenalaan, sivuaineeseen tai harrastukseen liittyvät hyötyohjelmat
  * Yksinkertainen fysiikkasimulaattori
  * DNA-ketjujen tutkija 
  * Keräilykorttien hallintajärjestelmä
  * Fraktaaligeneraattori

Voit katsoa myös [vanhat esimerkkiaiheet](https://www.cs.helsinki.fi/node/59273), jotka tosin ovat suurimmaksi osaksi samoja.


###




## GitHubissa olevan repositorion kloonaaminen

Teimme äsken repositorion ensin paikallisesti ja linkitimme sen GitHubissa olevaan etärepositorioon. Usein tilanne on sellainen, missä haluaisimme GitHubissa jo olevan repositorion omalle koneellemme. Tähän on tarkoitettu gitin komento clone.

* Luo GitHubiin uusi repositorio, laita tällä kertaa rasti kohtaan "Initialize this repository with a README"
* GitHub luo repositorion sisälle README.md:n
* Lisää githubista repositorioon uusi tiedosto ja tee jotain muutoksia README.md:hen
* klikkaa kohtaa _clone or download_ ja kopioi kloonausurl
  * varmista että valittuna on "clone with SSH"

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-4.png" alt="alt text" width="400">

* mene sopivaan hakemistoon paikallisella koneella
  * **ÄLÄ** kuitenkaan mene minkään git-repositorion sisälle
* anna kloonauskomento, parametrina kloonausurl

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

Hakemistoosi syntyy uusi hakemisto, esimerkissä nimeltään _otm2016-uusi_, eli oletusarvoisesti nimi päätellään kloonausurlista. Uuden hakemiston nimen voi myös määritellä itse antamalla komennolle lisäparametrin:

``` 
git clone git@github.com:mluukkai-cs/otm2016-uusi.git hakemiston_nimi
``` 

Syntynyt hakemisto on nyt git-repositorio, jonka sisältö on sama kuin etärepositoriossa.
* tee repositorioon jokin muutos, lisää ja committoi
* push muutokset githubiin
* varmista GitHubista että muutos menee perille