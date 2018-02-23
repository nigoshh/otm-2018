## matotiedosto GitHubissa

Jos GitHubiin päätyi matotiedosto gitignorauksesta huolimatta, pyydä ohjaajalta neuvoa miten saat sen pois... GitHubiin ei kannata laittaa mitään matotiedostojen tapaista roskaa, ne antavat erittäin epäammattilaismaisen vaikutelman.


## turhien tiedostojen ignorointi

Monet ohjelmat generoivat tiedostoja ja hakemistoja omien konfiguraatioidensa ym. tallentamista varten. Yleensä ei ole mielekästä tallettaa niitä git-repositorioon joten ne on syytä määritellä [.gitignore](https://github.com/mluukkai/OTM2016/wiki/Viikon-3-paikanpaalla-tehtavat#gitignore)-tiedostossa ignoroitavaksi.

Käytetään nyt hieman graafista gedit-editoria. Avaa gedit ja varmista asetuksista (edit/preferences, huomaa että valikko löytyy laitoksen koneilla koko **ruudun yläosasta**), että se on määritelty tekemään automaattisia backup-tiedostoja

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-1.png" alt="alt text" width="400">

**HUOM** tee komennot täsmälleen ohjeen mukaisessa järjestyksessä

* editoi tiedostoa README.md geditillä
  * lisää tekstiin esim. _blockquote_
* talleta muutokset
  * **ÄLÄ** lisää ja commoittoi muutoksia vielä!
  * vaan vasta siinä vaiheessa kun kohta gitignoroimme madot
* tarkista nyt hakemiston tilanne (komennolla ls) sekä git status
* hakemistoon olisi pitänyt syntyä "matotiedosto" _README.md~_ 
  * matotiedoston pitäisi olla gitin suhteen tilassa _Untracked_
* kyseessä on geditin tiedoston vanhasta versiosta tekemä backup

Koska käytämme versionhallintaa, ei editorin tekemille backupeille ole käyttöä, versionhallintahan mahdollistaa paluun tiedoston vanhoihin versioihin.

* gitignoraa matotiedosto
  * eli tee hakemistoon tiedosto _.gitignore_ ja merkkaa siihen README.md~ ignoroitavaksi
* varmista nyt komennolla _git status_ että README.md:n matoversio on ignoroitu
* lisää ja commitoi tiedosto .gitignore

* Tee repositoriosi sisälle uusi hakemisto _dokumentointi_ ja sen sisälle tiedosto _kaytto-ohje.md_ kirjoita tiedostoon jotain
* lisää ja commitoi muutokset
* editoi käyttöohjetta gedit-editorilla
* huomaat, että jälleen syntyy matotiedosto

Ei ole käytännöllistä lisätä .gitignore-tiedostoon erikseen jokaista erillistä matotiedostoa. Onneksi voimme määritellä ignoroitavksi _tiedostopatternin_ eli joukon samaan tapaan nimettyjä tai samassa hakemistossa sijaitsevia tiedostoja.
* määrittele ignoroitavaksi repositorion kaikki tiedostot, joiden nimi päättyy matoon eli merkkiin ~
* ohjeen sopivan tiedostopatternin tekemiseksi löydät [täältä](https://www.atlassian.com/git/tutorials/gitignore/#git-ignore-patterns)
* varmista, että käyttöohjeen mato ei näy git statuksessa
* tee joku uusi tiedosto repositorioon, editoi sitä tallennuksen jälkeen ja tallenna uudelleen 
* varmista että mato ei tule versionhallinnan piiriin
* lisää ja commitoi muutokset repositorioon

Vaikka käytimme nyt gedit-editoria, kyseessä on niin **huono editori**, että sen käyttö ei ole suositeltavaa (esim. ohjelmoitaessa). Parempia editoreja ovat esim. [Atom](https://atom.io) ja [sublime text](https://www.sublimetext.com).
