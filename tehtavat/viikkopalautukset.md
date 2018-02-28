# viikkopalautukset

## viikko 2 

Palautuksen deadline ma 26.3. klo 23:59

Palautus tapahtuu lisämällä oman aiheen alustava _määrittelydokumentti_ palautusrepositorioon

Määrittelydokumentti tehdään samaan tapaan kuin [referenssiprojektista](https://github.com/mluukkai/OtmTodoApp) eli [markdown](https://guides.github.com/features/mastering-markdown/)-muodossa, sijoitetaan repositorion hakemistoon _dokumentointi_ ja siihen tulee olla linkki repositorion README.md:stä

Määrittelydokumenttiin voi ottaa mallia [referenssiprojektista](https://github.com/mluukkai/OtmTodoApp). 

# TÄSTÄ ASTI KESKENERÄISTÄ

## viikko 3

Palautuksen deadline ma 9.4. klo 23:59

- Koodin runko valmiina (2p)
  - Edellytys pisteille ajettavissa oleva versio, joka toteuttaa ainakin osan jostain toiminnallisuudesta

## viikko 4

Palautuksen deadline ma 16.4. klo 23:59

- Ohjelman perustoiminnallisuus (1p)
  - Lisää koodia edellisestä viikosta 
- Testien aloitus (1p)
- Alustava rakenne luokkakaavona (0.5p)
- Checkstyle otettu käyttöön (0.5p)

## viikko 5

Palautuksen deadline ma 23.4. klo 23:59

- Release 1 (1p)
  - releasessa oltava suoritettava jar
  - Koodi kasvanut edellisestä viikosta
- Testejä lisää (1p)
  - Testikattavuusraportti
- Jotain päätoiminnallisuutta kuvaava sekvenssikaavio (1p)
- Koodikatselmointi

Ohjeita
- [testikattavuuden määrittly](https://github.com/mluukkai/otm-2018/blob/master/web/javadoc.md)

### Github release

Yksi mahdollisuus on luoda GitHubiin release, eli julkaistu versio.
* klikkaa repositorion GitHub-sivulta kohtaa "0 releases"
* määrittele julkaisun tiedot ja lisää jar-tiedosto klikkaamalla kohtaa "Attach binaries..."
  * jar-tiedosto kannattaa ehkä uudelleennimetä, mavenin generoima tiedostonimi on hieman ikävä

<img src="https://github.com/mluukkai/otm2016/raw/master/img/lh5-6.png" alt="alt text" width="800">

Nyt koodi on kenen tahansa ladattavissa menemällä GitHub-repositorioosi, ja klikkaamalla repositoriosivusi kohtaa "1 release" ja suoritettavissa komennolla <code>java -jar tiedostonnimi.jar</code> olettaen että koneelle on asennettu Javan versio 1.8

## viikko 6

Palautuksen deadline ma 30.4. klo 23:59

- Release 2 (1p)
  - releasessa oltava suoritettava jar
  - Koodi kasvanut edellisestä viikosta
- Testejä lisää (0.5p)
  - testikattavuusraportti
- JavaDoc aloitettu (0.5p)
- Alustava versio arkkitehtuuridokumentista (1p)

Ohjeita
- [JavaDoc](https://github.com/mluukkai/otm-2018/blob/master/web/javadoc.md)

## viikko 7