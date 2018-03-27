# harjoitustyö, viikko 3

Palautuksen deadline ti 10.4. klo 23:59

Muista pushata  harjoitustyöhön liittyvät asiat GitHubiin ennen viikkodeadlinea.
- Jos pushaus tapahtuu myöhässä, mutta deadlinea seuraavaan aamuun klo 07 mennessä, saat viikkopisteet vähennettynä yhdellä. 
- Klo 07 jälkeen tulevia repositorion päivityksiä ei huomioida pisteytyksessä, eli ne tuovat 0 pistettä.

Palautuksesta on tarjolla 2 kurssipistettä.

Arvostelussa kiinnitetään huomiota seuraaviin seikkoihin
- Repostitorion juuresta löytyy Maven-projekti
  - [ohje](https://github.com/mluukkai/otm-2018/blob/master/web/tyon_aloitus.md#harjoitusty%C3%B6n-aloitus) projektin luomiseen ja sen  sijoittamiseen palautusrepositoriossa 
  - jos teet projektisi jollain muulla kielellä, tee projekti valitsemasi kielen mavenia vastaavalla mekanismilla
- Projektin koodin pystyy suorittamaan NetBeansin vihreällä napilla _tai_ komennolla _mvn compile exec:java -Dexec.mainClass=pakkaus.Paaohjelma_
  - maven-komennon parametrina tulee olla metodin _main_ sisältävän luokan täydellinen, eli myös pakkauksen sisältämä nimi.
  - [referenssisovelluksen](https://github.com/mluukkai/OtmTodoApp) tapauksessa parametri olisi _-Dexec.mainClass=todoapp.ui.TodoUi_
- Edellytys pisteille suoritettavissa oleva versio, joka toteuttaa ainakin osan jostain määrittelydokumentin toiminnallisuudesta
  - Pelkät getterietä ja settereitä sisältävät, täysin ilman toiminnallisuutta olevat luokat eivät tuo pisteitä
- Sovelluksella on oltava _vähintään yksi testi_ jonka voi suorittaa komennolla _mvn test_
- Sovellukselle tulee pystyä generoimaan testikattavuusraportti komennolla _mvn test jacoco:reportt_
- Tuntikirjanpito on ajantasalla
  - Tuntikirjanpitoon ei merkitä laskareihin käytettyä aikaa
- Repositorion README.md kunnossa
  - tiedosto on kurssin tämän vaiheen osalta relevantin sisällön suhteen samankaltainen  kuin [referenssisovelluksen](https://github.com/mluukkai/OtmTodoApp) README
  - kaikki ylimääräinen, mm linkit laskareihin on poistettu (laskarit voi jättää hakemiston _laskarit_ alle)
- Repositorio siisti
  - ei ylimääräistä tavaraa (mm. hakemistoa target)
  - järkevä .gitignore-tiedosto olemassa