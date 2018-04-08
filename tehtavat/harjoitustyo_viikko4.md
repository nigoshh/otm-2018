# Harjoitustyö, viikko 4

Palautuksen deadline ti 17.4. klo 23:59

Muista pushata  harjoitustyöhön liittyvät asiat GitHubiin ennen viikkodeadlinea.
- Jos pushaus tapahtuu myöhässä, mutta deadlinea seuraavaan aamuun klo 07 mennessä, saat viikkopisteet vähennettynä yhdellä. 
- Klo 07 jälkeen tulevia repositorion päivityksiä ei huomioida pisteytyksessä, eli ne tuovat 0 pistettä.

Palautuksesta on tarjolla 3 kurssipistettä.

Arvostelussa kiinnitetään huomiota seuraaviin seikkoihin

- Ohjelma on kasvanut edellisest viikosta (0.75p)
  - Projektin koodin pystyy suorittamaan NetBeansin vihreällä napilla _tai/ja_ komennolla <code>mvn compile exec:java -Dexec.mainClass=pakkaus.Paaohjelma</code>
  - Ohjelmasta on olemassa suoritettava versio, joka on kasvanut edellisestä viikosta _ja_ toteuttaa edellisen viikon versiota suuremman osan määrittelydokumentin toiminnallisuudesta
- Testaus on edennyt (0.5p)
  - Sovellukselle tulee pystyä generoimaan testikattavuusraportti komennolla <code>mvn test jacoco:report</code>
  - Käyttöliittymän rakentava koodi [jätetään pois](https://github.com/mluukkai/otm-2018/blob/master/web/maven.md#koodin-huomiotta-jättäminen-kattavuusraportissa) testikattavuusraportista
  - Sovelluksen testien rivikattavuuden tulee olla vähintään 20%
  - Jos teet projektisi jollain muulla kielellä kuin Javalla, lisää README-tiedostoon ohje testien suorittamiselle ja kattavuusraportin generoimiselle
- Koodin laatu (1p)
  - Sovelluslogiikka on riittämässä määrin eriytetty käyttöliittymästä
    - Vihjeitä [https://github.com/mluukkai/otm-2018/blob/master/web/java.md](täällä) ja [referenssisovelluksessa](https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/arkkitehtuuri.md)
  - Ohjelman [pakkausrakenne](https://github.com/mluukkai/otm-2018/blob/master/web/koodin_laatuvaatimukset.md#5-pakkaukset) heijastaa ohjelman loogista rakennetta ja nimennältään järkevä
  - Checkstyle on otettu käyttöön 
    - Ohje Checkstylen käyttöönottoon [täällä](https://github.com/mluukkai/otm-2018/blob/master/web/checkstyle.md)
    - Täydet pisteet Checkstylestä ainoastaan jos ohjelmassa on alle 10 Checkstyle-virhettä
    - Käyttöliittymän rakentavan koodin ei tarvitse olla Checkstyle-tarkastelun alla
    - Jos teet projektisi jollain muulla kielellä kuin Javalla, ota käyttöön kielen _Checkstyleä_ vastaava työkalu, määrittele se järkevästi ja laita README-tiedostoon ohje tyylitarkastusten suorittamisele
- Ohjelman alustava rakenne luokka/pakkauskaavona (0.75p) 
vastaavalla mekanismilla
  - Kaavion ei tarvitse merkitä kuin sovelluslogiikan kannalta oleelliset luokat
  - Voit tarvittaessa tehdä kaavion, josta ilmenee myös sovelluksen [pakkausrakenne](https://github.com/mluukkai/otm-2018/blob/master/web/materiaali.md#pakkauskaavio)
  - Mallia voi ottaa [referenssisovelluksesta](https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/arkkitehtuuri.md#sovelluslogiikka)
  - Tee repositorioosi hakemist _dokumentaatio_ ja sen sisälle tiedosto _arkkitehtuuri.md_ ja upota kuva tiedostoon, tiedoston sisältö voi olla muilta osin tyhjä
  - Tiedostoon _arkkitehtuuri.md_ tulee olla linkki repositorion README:stä [referenssisovelluksen](https://github.com/mluukkai/OtmTodoApp) tavoin
 
Seuraavien kohtien puutteet vähentävät pisteitä

- Tuntikirjanpito on ajantasalla
  - Tuntikirjanpitoon ei merkitä laskareihin käytettyä aikaa
- Repositorion README.md kunnossa
  - tiedosto on kurssin tämän vaiheen osalta relevantin sisällön suhteen samankaltainen  kuin [referenssisovelluksen](https://github.com/mluukkai/OtmTodoApp) README.md
  - kaikki ylimääräinen, mm. linkit laskareihin on poistettu 
- Repositorio siisti
  - ei ylimääräistä tavaraa (mm. hakemistoa target)
  - laskarit jätetään hakemiston _laskarit_ alle
  - järkevä .gitignore-tiedosto olemassa
