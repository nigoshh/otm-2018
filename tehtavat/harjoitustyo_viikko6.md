# KESKEN

## harjoitustyö, viikko 6

Palautuksen deadline keskiviikko 2.5. klo 23:59

HUOM
- koodikatselmointi, deadline ...
- loppudeadline ... vaatimukset


Arvostelussa kiinnitetään huomiota seuraaviin seikkoihin

- Ohjelma on kasvanut edellisestä viikosta (0.75p)
  - Ohjelman suoritettavissa olevasta versiosta on tehty uudi [GitHub-release](https://github.com/mluukkai/otm-2018/blob/master/web/release.md), joka sisältää suoritettavan version jar-tiedoston ja muut mahdolliset ohjelman suorituksessa tarvittavat tiedostot
  - Ohjelmasta pystyy tekemään suorituskelpoisen [jar](https://github.com/mluukkai/otm-2018/blob/master/web/maven.md#jarin-generointi)-tiedoston komennolla _mvn package_
  - Ohjelman suoritettavissa oleva versio on kasvanut edellisestä viikosta _ja_ toteuttaa edellisen viikon versiota suuremman osan määrittelydokumentin toiminnallisuudesta
- Koodin laatu (0.5p)
  - Ohjelma ei sisällä suurta määrää toisteista koodia
  - Ohjelman luokkarakenne on järkevä
    - luokkien tulee pyrkiä noudattamaan ns. [single responsibility] (https://materiaalit.github.io/ohjelmointi-s17/part6/) -periaatetta, eli yhden luokan ei tulisi tehdä liian montaa asiaa
  - Metodit ovat järkevän pituisia ja myös yhteen asiaan keskittyviä  
- Testaus on edennyt (0.5p)
  - Sovellukselle tulee pystyä generoimaan testikattavuusraportti komennolla <code>mvn test jacoco:report</code>
    - Käyttöliittymän rakentava koodi [jätetään pois](https://github.com/mluukkai/otm-2018/blob/master/web/maven.md#koodin-huomiotta-jättäminen-kattavuusraportissa) testikattavuusraportista
  - Sovelluksen testien rivikattavuuden tulee olla vähintään 50%
  - Testien tulee testata järkevällä tavalla ohjelman toiminnallisuutta
    - jos testit on tehty pelkästään rivikattavuuden saatuttamiseksi, ei testeistä saa pisteitä
- JavaDoc aloitettu (0.5p)
  - [ohje](https://github.com/mluukkai/otm-2018/blob/master/web/javadoc.md) JavaDocin käyttöön
  - ainakin osalle ohjelman luokista ja niiden metodeista on tehty JavaDoc-kuvaukset
  - JavaDoc tulee olla generoitavissa komennolla _mvn javadoc:javadoc_
  - edellytyksenä pisteille on vähintään 5 luokan ja sen julkisten metodien dokumentointi
- Alustava arkkitehtuurikuvaus (0.5p)
  - Dokumentti sisältää sovelluksen korkean tason (esim. pakkausten tasolla) rakenteen kuvauksen, sekä alustavan kuvauksen sovelluslogiikasta
  - Dokumentissa kannattaa hyödyntää edellisten viikkojen kaavioita
  - Mallia voi ottaa [referenssisovelluksesta](https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/arkkitehtuuri.md#sovelluslogiikka)
  - Dokumentin alustavan version sopiva pituus tässä vaiheessa on noin 1-2 sivua
- Alustava käyttöohje (0.25p)
  - Dokumentin alustavan version sopiva pituus tässä vaiheessa on noin sivu
  - Ohje voi olettaa, että sovellusta suoritetaan palautusrepositoriosta käsin, eli asentamiseen ja konfigurointiin ei ole vielä tarvetta ottaa kantaa
  - Mallina voi jälleen toimia[referenssisovellus](https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/kayttoohje.md)

**Seuraavien kohtien puutteet vähentävät pisteitä**

- Koodin laatu
  - Pakkausrakenne järkevä (esim. kaikki koodi oletuspakkauksessa)
  - Sovelluslogiikkaa on eriytetty riittävästi käyttöliittymästä
  - Checkstyle on käytössä
    - Ohjelmassa on alle 5 Checkstyle-virhettä
    - Käyttöliittymän rakentavan koodin ei tarvitse olla Checkstyle-tarkastelun alla
    - Jos teet projektisi jollain muulla kielellä kuin Javalla, tulee olla käytössä kielen _Checkstyleä_ vastaava työkalu, määrittele se järkevästi ja laita README-tiedostoon ohje tyylitarkastusten suorittamiselle
- Tuntikirjanpito on ajantasalla
  - **Tuntien summan tulee olla merkittynä**
  - Tuntikirjanpitoon ei merkitä laskareihin käytettyä aikaa
- Repositorion README.md kunnossa
  - tiedosto on kurssin tämän vaiheen osalta relevantin sisällön suhteen samankaltainen kuin [referenssisovelluksen](https://github.com/mluukkai/OtmTodoApp) README.md, eli siellä on ainakin seuraavat
    - harjoitustyön aiheen lyhyt kuvas
    - linkit vaatimusmäärittelyyn, arkkitehtuuridokumenttiin, käyttöohjeeseen ja tuntikirjanpitoon 
    - linkki releaseihin
    - ohjeet komentoriviltä suoritettaviin toimenpiteisiin (testaus, testiraporsin suoritus, suoritettavan jarin generointi, checkstyleraportin suorittaminen)
- Repositorio siisti
  - ei ylimääräistä tavaraa (mm. hakemistoa target)
  - laskarit jätetään hakemiston _laskarit_ alle
  - järkevä .gitignore-tiedosto olemassa