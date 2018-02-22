# Ohjelmistotekniikan menetelmät kevät 2018

Keväästä 2018 alkaen Ohjelmistotekniikan menetelmät (eli OTM) siirtyy aineopintoihin. Kurssin esitietoina on Ohjelmoinnin jatkokurssi sekä Tietokantojen perusteet. Oletuksena on, että molemmista kursseista on käyty suhteellisen tuore versio ja että molempien aihepiiri on vielä hyvin mielessä.

Kurssin oppimistavoitteet ovat edelleen suunilleen samat kuin aiemmin. Kurssin suoritettuaan opiskelija
- Tuntee ohjelmistotuotantoprosessin vaiheet
- On tietoinen vesiputousmallin ja ketterän ohjelmistotuotannon luonteesta
- Osaa soveltaa versionhallintaa osana ohjelmistokehitystä
- Osaa soveltaa UML-mallinnustekniikkaa vaatimusmäärittelyssä ja ohjelmiston suunnittelussa tarkoituksenmukaisella tavalla
- Tuntee ohjelmiston testauksen eri vaiheet
- Osaa soveltaa automatisoitua testausta yksinkertaisissa ohjelmistoprojekteissa
- Tuntee tärkeimpiä ohjelmiston suunnitteluperiaatteita ja osaa soveltaa niitä yksinkertaisissa projekteissa

Kurssin suoritusmuoto poikkeaa radikaalisti aiemmasta viikoittaiset luennot ja laskuharjoitukset sisältävästä kurssista, nykyinen OTM muistuttaakin läheisesti entistä Ohjelmoinnin harjoitustyötä.

Kurssin ensimmäisen kahden viikon aikana harjoitellaan versionhallintaa, yksikkötestausta sekä UML-kaavioiden tekemistä. Toisesta viikosta alkaen aloitetaan oman harjoitustyön tekeminen. Harjoitustyön tekemisen ohessa osoitetaan riittävä osaaminen kurssin oppimistavoitteiden suhteen. Koetta kurssilla ei ole.

# Ohjelmistotuotanto

Kun tehdään pientä ohjelmaa omaan käyttöön ei työskentelymenetelmillä ole suurta merkitystä. Kun ohjelmiston koko on suurempi ja erityisesti jos sitä tehdään useamman ihmisen toimesta ulkoiselle käyttäjälle tai asiakkaalle ei pelkkä häkkeröinti enää tuota optimaalista tulosta. Tarvitaankin jonkinlainen systemaattinen menetelmä ohjaamaan ohjelmistokehittäjien toimintaa ja varmistamaan, että ohjelmistosta tulee käyttäjien käyttötarkoitukseen sopiva.

Ohjelmiston systemaattinen tekeminen, eli ohjelmistotuotanto (engl. Software engineering) sisältää useita erilaisia aktiviteettejä joiden aikana tekemisen fokus on hieman erilaisissa asioissa. Näitä aktiviteetteja tai vaiheita niinkuin niitä joskus nimitetään ovat seuraavat

- _vaatimusmäärittely_ jonka tehtävä on selvittää mitä ohjelmiston halutaan toimivan
- _suunnittelu_ jonka aikana mietitään miten halutunkaltainen ohjelmisto tulisi rakentaa
- _toteutusvaiheessa_ määritelty ja suunniteltu ohjelmisto koodataan
- _testauksen_ tehtävä taas on varmistaa ohjelmiston laatu, että se ei ole liian buginen ja että se toimii kuten vaatimusmäärittely sanoo
- _ylläpitovaiheessa_ ohjelmisto on jo käytössä ja siitehen tehdään bugikorjauksia ja mahdollisia laajennuksia.

Katsotaan vielä kutakin vaihetta hieman tarkemmin. 

Käytetään seuraavassa esimerkkinä kurssia varten tehtyä yksinkertaista [todo](https://github.com/mluukkai/OtmTodoApp)-sovellusta.


## Vaatimusmäärittely

Vaatimusmäärittelyn aikana kartoitetaan ohjelman tulevien käyttäjien tai tilaajan kanssa se, mitä toiminnallisuutta ohjelmaan halutaan. Ohjelman toiminnalle siis asetetaan asiakkaan haluamat vaatimukset. Tämän lisäksi kartoitetaan ohjelman toimintaympäristön ja toteutusteknologian järjestelmälle asettamia rajoitteita.

Vaatimusmäärittelyn tuloksena on useimmiten jonkinlainen dokumentti, johon vaatimukset kirjataan. Dokumentin muoto vaihtelee suuresti, se voi olla paksu mapillinen papereita tai vaikkapa joukko postit-lappuja.

### Todo-sovelluksen vaatimusmäärittely

Esimerkkisovelluksemme on siis klassinen _todoapp_, eli sovellus, jonka avulla käyttäjien on mahdollista pitää kirjaa omista tekemättömistä töistä, eli _todoista_.

Vaatimusmäärittely kannattaa yleensä aloittaa tunnistamalla järjestelmän erityyppiset käyttäjäroolit. Sovelluksellamme ei ole toistaiseksi muuta kuin normaaleja käyttäjiä. Jatkossa sovellukseen saatetaan lisätä myös ylläpitäjän oikeuksilla varustettu käyttäjärooli.

Kun sovelluksen käyttäjäroolit ovat selvillä, mietitään mitä toiminnallisuuksia kunkin käyttäjäroolin halutaan pystyvät tekemään sovelluksen avulla.

Todo-sovelluksen normaalien käyttäjien toiminnallisuuksia ovat esim. seuraavat

- käyttäjä voi luoda järjestelmään käyttäjätunnuksen
- käyttäjä voi kirjautua järjestelmään
- kirjautumisen jälkeen käyttäjä näkee omat tekemättömät työt eli todot
- käyttäjä voi luoda uuden todon
- käyttäjä voi merkitä todon tehdyksi, jolloin todo häviää listalta

Ylläpitäjän toiminnallisuuksia voisivat olla esim. seuraavat

- ylläpitäjä näkee tilastoja sovelluksen käytöstä
- ylläpitäjä voi poistaa normaalin käyttäjätunnuksen

Ohjelmiston vaatimuksiin kuuluvat myös _toimintaympäristön rajoitteet_. Todo-sovellusta koskevat seuraavat rajoitteet
- ohjelmiston tulee toimia Linux- ja OSX-käyttöjärjestelmillä varustetuissa koneissa

Vaatimusmäärittelyn aikana hahmotellaan yleensä myös sovelluksen käyttöliittymä.

Todo-sovelluksen alustava vaatimusmäärittely kokonaisuudessaan
[täällä](https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/vaatimusmaarittely.md).

## Suunnittelu

Ohjelmiston suunnittelu jakautuu yleensä kahteen erilliseen vaiheeseen.

Arkkitehtuurisuunnittelussa määritellään ohjelman rakenne karkealla tasolla eli mistä suuremmista rakennekomponenteista ohjelma koostuu, iten komponentit yhdistetään, eli minkälaisia komponenttien väliset rajapinnat sekä mitä riippuvuuksia ohjelmalla on esim. tietokantoihin ja ulkoisiin rajapintoihin.

Arkkitehtuurisuunnittelua tarkentaa oliosuunnittelu, missä mietitään ohjelmiston yksittäisten komponenttien rakennetta,  eli minkälaisisista luokista komponentot koostuvat ja  miten luokat kutsuvat toistensa metodeja sekä mitä apukirjastoja luokat käyttävät.

Myös ohjelmiston suunnittelu, erityisesti sen arkkitehtuuri dokumentoidaan usein jollain tavalla. Joskus tosin dokumentaatio on hyvin kevyt tai voi jopa puuttua kokonaan ja ajatellaankin että hyvin muotoiltu koodi voi korvata dokumentoinnin.

### Kerrosarkkitehtuuri

### Todo-sovelluksen suunnittelu

Todo-sovelluksen arkkitehtuurikuvaus
[täällä]https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/arkkitehtuuri.md).


## Testaus

## Vesiputousmalli

## Ketterä ohjelmistokehitys

# Työkaluja

## Komentorivi

## Versionhallinta

## Maven

## UML

## Luokkakaaviot

## Sekvenssikaaviot

## pakkauskaavio

# Toteutukseen ja suunnitteluun liittyviä asioita

## Single responsibility -periaate