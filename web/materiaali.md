# EI AJANTASALLA, lukeminen omalla vastuulla

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

## Testaus

Toteutuksen yhteydessä ja sen jälkeen järjestelmää testataan. Testausta on monentasoista. _Yksikkötestauksessa_ (engl. unit testing) tutkitaan yksittäisten metodien ja luokkien toimintaa. Yksikkötestauksen tekee usein testattavan komponentin ohjelmoija. Kun erikseen ohjelmoidut komponentit (eli luokat tai luokkakokoelmat) yhdistetään, suoritetaan _integrointitestaus_ (engl. integration testing), jossa varmistetaan erillisten komponenttien yhteentoimivuus. Integrointitestauksessa testauksen kohteena ovat erityisesti suunnitteluvaiheessa erillisten komponenttien välille määritellyt rajapinnat. _Järjestelmätestauksessa_ (engl. system testing) testataan järjestelmää kokonaisuutena ja verrataan, että se toimii vaatimusdokumentissa sovitun määritelmän mukaisesti.

## Vesiputousmalli

Ohjelmistoja on perinteisesti tehty vaihe vaiheelta etenevän _vesiputousmallin_ (engl. waterfall model) mukaan. Vesiputousmallissa edellä esitellyt ohjelmistotuotannon vaiheet suoritetaan peräkkäin:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-1.png)

Vesiputousmallissa suoritetaan siis ensin vaatimusmäärittely, jonka seurauksena kirjoitetaan vaatimusdokumentti, johon pyritään kokoamaan kaikki ohjelmalle osoitettavat vaatimukset mahdollisimman tarkasti dokumentoituna. Määrittelyvaiheen päätteeksi vaatimusdokumentti jäädytetään. Jäädytettyä vaatimusmäärittelyä käytetään usein ohjelman kehittämisen vaatimien resurssien arvioinnin perustana ja myös sopimus ohjelman hinnasta saatetaan tehdä vaatimusmäärittelyn pohjalta.

Vaatimusmäärittelyä seuraa suunnitteluvaihe, joka myös dokumentoidaan tarkoin. Pääsääntöisesti suunnitteluvaiheen aikana ei enää tehdä muutoksia määrittelyyn. Joskus tämäkin on tarpeen. Suunnittelu pyritään tekemään niin täydellisenä, että ohjelmointivaiheessa ei enää ole tarvetta muuttaa suunnitelmia.

Suunnittelun jälkeen toteutetaan ohjelman yksittäiset komponentit ja tehdään niille yksikkötestaus. Tämän jälkeen erilliset komponentit liitetään yhteen eli integroidaan ja suoritetaan integrointitestaus. 

Integroinnin jälkeen ohjelmalle tehdään järjestelmätestaus, eli testataan, että ohjelmisto toimii kokonaisuutena niin kuin määrittelydokumentissa on määritelty.

Vesiputousmalli on monella tapaa ongelmallinen. Mallin toimivuus perustuu siihen oletukseen, että ohjelman vaatimukset pystytään määrittelemään täydellisesti ennen kuin suunnittelu ja ohjelmointi alkaa. Näin ei useinkaan ole. On lähes mahdotonta, että asiakkaat pystyisivät tyhjentävästi ilmaisemaan kaikki ohjelmalle asettamansa vaatimukset. Vähintäänkin riski sille, että ohjelma on käytettävyydeltään huono, on erittäin suuri. Usein käy myös niin, että vaikka ohjelman vaatimukset olisivat kunnossa vaatimusten laatimishetkellä, muuttuu toimintaympäristö (tapahtuu esim. yritysfuusio) ohjelman kehitysaikana niin ratkaisevasti, että valmistuessaan ohjelma on vanhentunut. Hyvin yleistä on myös se, että vasta käyttäessään valmista ohjelmaa asiakkaat alkavat ymmärtää, mitä he olisivat ohjelmalta halunneet.

Asiakkaan muuttuvien vaatimuksien lisäksi toinen suuri ongelma on se, että vesiputousmallissa ohjelmistoa aletaan testata verrattain myöhäisessä vaiheessa. Erityisesti integraatiotestauksessa on tyypillistä että ohjelmasta löydetään pahoja ongelmia, joiden korjaaminen hidastaa ohjelmiston valmistumista paljon ja käy kalliiksi. 

## Ketterä ohjelmistokehitys

Vesiputousmallin heikkoudet ovat johtaneet viime vuosina yleistyneiden _ketterien (engl. agile) ohjelmiston kehitysmenetelmien_ kehittelyyn ja käyttöönottoon. 

Ketterissä menetelmistä lähdetään oletuksesta, että vaatimuksia ei voi tyhjentävästi määritellä ohjelmistokehitysprosessin alussa. Koska näin ei voida tehdä, ei sitä edes yritetä vaan pyritään toimimaan niin, että ohjelmista saadaan toimivia jatkuvasti muuttuvista vaatimuksista huolimatta.

Ketterä ohjelmistokehitys etenee yleensä siten, että ensin kartoitetaan pääpiirteissään ohjelman vaatimuksia ja ehkä hahmotellaan järjestelmän arkkitehtuuri pääpiirteittäin. Tämän jälkeen suoritetaan useita _iteraatioita_ (joista käytetään yleisesti myös nimitystä sprintti), joiden kunkin aikana järjestelmään valitaan suunniteltavaksi ja toteutettavaksi osa järjestelmän vaatimuksista. Vaatimukset voivat tarkentua koko prosessin ajan.

Yksittäinen iteraatio, joka on kestoltaan tyypillisesti 1-4 viikkoa, siis lisää järjestelmään pienen osan koko järjestelmän toivotusta toiminnallisuudesta. Tyypillisesti tärkeimmät ja toteutuksen kannalta haasteellisimmat ja riskialttiimmat toiminnallisuudet toteutetaan ensimmäisillä iteraatioilla. Yksi iteraatio sisältää toteutettavaksi valittujen vaatimusten tarkennuksen, suunnittelun, toteutuksen sekä testauksen. 

Jokainen iteraatio tuottaa toimivan ja toteutettujen ominaisuuksien kannalta testatun järjestelmän. Asiakas pääsee testaamaan järjestelmää jokaisen iteraation jälkeen. Tällöin voidaan jo aikaisessa vaiheessa todeta, onko kehitystyö etenemässä oikeaan suuntaan ja vaatimuksia voidaan tarvittaessa tarkentaa ja lisätä.

Jokainen iteraatio siis sisältää määrittelyä, suunnittelua, ohjelmointia ja testausta ja jokaisen iteraation jälkeen saadaan asiakkaalta palautetta siitä, onko kehitystyö etenemässä oikeaan suuntaan:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-1.png)

Ketterässä ohjelmistokehityksessä dokumentointi ei ole yleensä niin keskeisessä osassa kuin perinteisissä menetelmissä.

Vähäisemmän dokumentaation sijaan testauksella ja ns. jatkuvalla integroinnilla on hyvin suuri merkitys. Yleensä pyritään siihen, että järjestelmään lisättävät uudet komponentit testataan välittömästi ja pyritään heti integroimaan kokonaisuuteen, tästä työskentelytavasta käytetään nimitystä _jatkuva integrointi_ (engl. continuous integration). Näin uusia versioita järjestelmästä syntyy jopa päivittäin iteraatioiden toteutusvaiheiden aikana.

Uusien komponenttien toimiminen pyritään varmistamaan perinpohjaisella automaattisella testauksella. Joskus jopa "testataan ensin", eli jo ennen ennen uuden komponentin toteuttamista ohjelmoidaan komponentin toimintaa testaavat testitapaukset. Testitapausten valmistuttua toteutetaan komponentti ja siinä vaiheessa kun komponentti läpäisee testitapaukset, se integroidaan muuhun kokonaisuuteen.

Erilaisia ketteriä ohjelmistokehitysmenetelmiä on olemassa lukuisia, näistä tunnetuin nykyään on Scrum. 

Ketterät menetelmät ovat nykyään vallitseva tapa tehdä ohjelmistoja. Ketterien menetelmien rinnalle ovat viime vuosina nousseet ketteryyden ideaa hieman jalostavat Lean-menetelmät. Palaamme aiheeseen tarkemmin kurssilla Ohjelmistotuotanto.

Tämän kurssin harjoitustyö pyritään tekemään osittain ketterien menetelmien hengessä, eli vaatimusmäärittely ja suunnittelu pidetään kevyenä ja ohjelmaa aletaan toteuttaa jo heti alkuvaiheessa. Ohjelmasta pyritään mahdollisuuksien mukaan tekemään jokaisen iteraation eli viikon päätteeksi toimiva versio jota sitten viikko viikolta laajennetaan. Kurssin vaatimaa dokumentaatiota tehdään osin matkan varrella.

# Työkaluja

Tarvitsemme ohejlmisokehityksessä suuren joukon käytännön työkaluja. 

## Komentorivi ja Versionhallinta

Olet jo ehkä käyttänyt muilla kursseilla komentoriviä ja versionohallintaa. 
Molemmat ovat aiheena viikon 1 [tehtävissä](https://github.com/mluukkai/otm-2018/blob/master/tehtavat/viikko1.md)

## Maven

Olet todennäköisesti ohjelmoinut Javaa suurimmaksi osaksi NetBeansilla ja luottanut siihen että kaikki hoituu valitsemalla sopivia toimintoja valikoista ja painamalla "vihreää nappia".

Alamme tämän kurssin myötä hieman tutkimaan miten Javalla tehdyn ohjelmiston hallinnointi (esim. koodin kääntäminen, koodin sekä tiestien suorittaminen ja koodin paketoiminen NetBeansin ulkopuolella suoritettavissa olevaksi jar-paketiksi) tapahtuu NetBeansin "ulkopuolella".

Java-projektien hallinnointiin on olemassa muutamakin vaihtoehto. Käytämme tällä kurssilla _mavenia_, joka lienee jo useimmille osittain tuttu esim. Tietokantojen perusteista.

[Ohje](https://github.com/mluukkai/otm-2018/blob/master/web/maven.md)
Mavenin käytön aloittamiseen.

## JUnit

Ohjelmistojen testaus tapahtuu nykyään ainakin yksikkö- ja integraatiotestien osalta automatisoitujen testityökalujen toimesta. Java-maailmassa testausta dominoi lähes yksinvaltiaan tavoin JUnit. Tulet kurssin ja myöhempienkin opintojesi aikana kirjoittamaan paljon JUnit-testejä. 

JUnitiin tutustumme viikon 2 [tehtävissä](https://github.com/mluukkai/otm-2018/blob/master/tehtavat/viikko1.md)

## JavaDoc

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-7.png)

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-8.png)

## Checkstyle

## UML

Ohjelmistojen dokumentoinnissa ja sovelluksen suunnittelun yhteydessä on usein tapana visualisoida ohjelman rakennetta tai toimintaperiaatetta UML-kaavioilla. UML tarjoaa lukuisia erilaisia kaaviotyyppejä, hyödynnämme kurssilla kuitenkin näistä ainoastaan kolmea.

### Luokkakaaviot

Kurssilla [Tietokantojen perusteet](https://materiaalit.github.io/tikape-k18/) olet jo tutustunut luokkakaavioiden käyttöön. 

Luokkakaavioiden käyttötarkoitus on ohjelman luokkien ja niiden välisten suhteiden kuvailu. Todosovelluksen oleellista tietosisältöä edustavat käyttäjää vastaava luokka _User_ : 

```java 
public class User {
    private String name;
    private String username;

    public User(String username, String name) {
        this.name = name;
        this.username = username;
    }

    public String getName() {
        return name;
    }

    public String getUsername() {
        return username;
    }              
}
```

ja tehtävää vastaava luokka _Todo_:

```java 
package todoapp.domain;

public class Todo {

    private int id;
    private String content;
    private boolean done;
    private User user;

    public Todo(int id, String content, boolean done, User user) {
        this.id = id;
        this.content = content;
        this.done = done;
        this.user = user;
    }
    
    public String getContent() {
        return content;
    }

    public User getUser() {
        return user;
    }

    public int getId() {
        return id;
    }

    public boolean isDone() {
        return done;
    }

    public void setDone() {
        done = true;
    }
}
```

Jokaiseen todoon liittyy yksi käyttäjä, ja yksittäiseen käyttäjään liittyviä todoja voi olla useita. Tilannetta kuvaa seuraava luokkakaavio

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-3.png)

Luokkakaavioon on nyt merkitty molempien luokkien attriuubuutit eli oliomuuttujat sekä metodit. 

Yleensä ei ole mielekästä kuvata luokkia tällä tarkkuudella, eli luokkakaavihin riittää merkitä luokan nimi

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-4.png)

Luokkien tarkemmat detaljit selviävät koodia katsomalla tai JavaDoc:ista.

#### riippuvuus

UML-kaavioissa olevat "viivat" kuvaavat luokkien olioiden välistä pysyvää yhteyttä. Joissain tilanteissa on mielekästä merkata kaavioihin myös ei-pysyvää suhdetta kuvaava katkoviiva, eli  _riippiipuvuus_.

Todosovelluksen soveluslogiikasta vastaa luokka _TodoService_ jonka koodi hieman lyhennettynä näyttää seuraavalta:

```java
public class TodoService {
    private TodoDao todoDao;
    private User loggedIn;
    
    public void createTodo(String content, User user) {
        Todo todo = new Todo(content, user);
        todoDao.create(todo);   
    }
    
    public List<Todo> getUndone() {
        if (loggedIn==null) {
            return new ArrayList<>();
        }
        
        return todoDao.getAll()
                .stream()
                .filter(t->{
                    return t.getUser().equals(loggedIn);
                })
                .filter(t->!t.isDone())
                .collect(Collectors.toList());
    }
    
		// ...
}
```

Sovelluslogiikaa hoitava olio tuntee kirjautuneen käyttäjän, mutta pääsee käsiksi kirjautuneen käyttäjän todoihin ainoastaan _todoDao_-olion välityksellä. Tämän takia luokalla ei ole yhteyttä luokkaan _Todo_, luokkien välillä on kuitenkin _riippuvuus_. Asia voidaan merkitä luokkakaavioon seuraavasti:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-5.png)

Riippuvuus siis kuvataan _katkoviivallisena nuolena_ joka kohdistuu siihen luokkaan mistä ollaan riippuvaisia. Riippuvuuteen ei merkitä numeroa toisin kuin yhteyteen.

#### rajapinta ja perintä

TodoService siis tuntee _TodoDao_-olion (jos unohdit mikä on DAO kertaa Tietokantojen perusteiden viikon 3 luku [2.4](https://materiaalit.github.io/tikape-k18/part3/)), jonka avulla se pääsee _todo_-olioihin. _TodoDao_ ei ole itseasiassa luokka vaan _rajapinta_: 

```java
public interface TodoDao {
    void create(Todo todo);
    List<Todo> getAll();
    void setDone(int id);
}
```

TodoDaosta voi olla olemassa useita eri toteutuksia. Tällä hetkellä ohjelmassa on _todo_-oliot tiedostoon tallettava _FileTodoDao_

```java
public class FileTodoDao implements TodoDao {
    public List<Todo> todos;
    private String file;

		// ...
}
```

sekä testien käyttämä _FakeTodoDao_. Jos ohjelmaa halutaan laajentaa siten, että tiedot talletetaan tiedostojen sijaan tietokantaan, voidaan tarkoitusta varten tehdä uusi toteutus rajapinnasta _SqlTodoDao_. 

Rajapinta ja sen toteuttavat luokat kuvataan luokkakaaviossa seuraavasti:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-6.png)

Samaa merkintätapaa eli valkoisen nuolenpään sisältävää viivaa käytetään perinnän merkitsemiseen. Esim. jos todosovelluksessa olisi normaalin käyttäjän eli luokan _User_ perivä ylläpitäjää kuvaava luokka _SuperUser_ merkattaisiin se luokkakaavioon seuraavasti:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-9.png)

### Pakkauskaavio

Todosovelluksen koodi on jaoiteltu _pakkausten_ avulla seuraavasti:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-10.png)

Pakkausrakenne voidaan kuvata UML:ssä pakkauskaaviolla:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-11.png)

Pakkauste välille on merkitty _riippuvuudet_ katkoviivalla. Pakkaus _todoapp.ui_ riippuu pakkauksesta _todoapp.domain_ sillä _ui_:n luokka _Main_ käyttää _domain_-pakkauksen luokkia _Todo_ ja _TodoService_.

Vastaavasti pakkaus _todoapp.domain_ riippuu pakkauksesta _todoapp.dao_ sillä domainin luokka _TodoService_ käyttää _dao_-pakkauksen rajapintoja _TodoDao_ ja UserDao.

Pakkauskaavioihin on myös mahdollista merkitä pakkausten siältönä olevia luokkia normaalin luokkakaaviosyntaksin mukaan:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-12.png)

Sovelluksen koodi on organisoitu _kerrosarkkitehtuurin_ periaatteiden mukaan. Asiasta lisää hieman myöhemmin tässä dokumentissa.

### Sekvenssikaaviot

Luokka- ja pakkauskaaviot kuvaavat ohjelman rakennetta. Ohjelman toimita ei kuitenkaan tule niistä ilmi millään tavalla. Tietokantojen perusteiden [viikolla 4](https://materiaalit.github.io/tikape-k18/part4/) on lyhyt maininta sekvenssikaavioista. 

Sekvenssikaaviot on alunperin kehitetty kuvaamaan verkossa olevien ohjelmien keskinäisen kommunikoinnin etenemistä. Sekvenssikaaviot sopivat kohtuullisen hyvin kuvaamaan myös sitä miten ohjelman oliot kutsuvat toistensa metodeja suorituksen aikana. 

Tarkastellaan seuraavaa ohjelmaa.

```java
public class Henkilo {
    private String nimi;
    private int palkka;
    private String tilinumero;

    public Henkilo(String nimi, int palkka, String tilinumero) {
        this.nimi = nimi;
        this.palkka = palkka;
        this.tilinumero = tilinumero;
    }
    
    public void setPalkka(int palkka) {
        this.palkka = palkka;
    }

    public int getPalkka() {
        return palkka;
    }

    public String getTilinumero() {
        return tilinumero;
    }       
}


public class Henkilostorekisteri {
    private Map<String, Henkilo> henkilot;
    private PankkiRajapinta pankki;

    public Henkilostorekisteri() {
        henkilot = new HashMap<String, Henkilo>();
        pankki = new PankkiRajapinta();
    }        
    
    public void lisaa(Henkilo henkilo){
        henkilot.set(henkilo, henkilo);
    }
    
    public void suoritaPalkanmaksu(){
        for (Henkilo henkilo : henkilot.values()) {
            String tiliNro = henkilo.getTilinumero();
            int palkka = henkilo.getPalkka();
            pankki.maksaPalkka(tiliNro, palkka);
        }
    }

    public void asetaPalkka(String nimi, int uusiPalkka){
        Henkilo h = hekilot.get(nimi);
				h.setPalkka(uusiPalkka);            
    }

}


public class PankkiRajapinta {

    public void maksaPalkka(String tilinumero, int summa) {
        // suorittaa maksun verkkopankin internet-rajapinnan avulla
        // yksityiskohdat piilotettu
    }
}
```

Sekvenssikaaviot kuvaavat yksittäisten suoritusskenaarioiden aikana tapahtuvia asioita. Kuvataan nyt seuraavan pääohjelman aikaansaamat tapahtumat:

```java
public static void main(String[] args) {
		Henkilostorekisteri rekisteri = new Henkilostorekisteri();
		
		Henkilo arto = new Henkilo("Hellas", 1500, "1234-12345");
		rekisteri.lisaa(arto);
		Henkilo sasu = new Henkilo("Tarkoma", 6500, "4455-123123");
		rekisteri.lisaa(sasu);      
		
		rekisteri.asetaPalkka("Hellas", 3500);   
		
		rekisteri.suoritaPalkanmaksu();
}
```

Sekvenssikaavio on seuraavassa:

![](https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/l-13.png)
 
Sekvenssikaaviossa oliot kuvataan laatikoina, joista lähtee viiva alaspäin. Kaavio alkaa tilanteesta, jossa _Henkilostorekisteri_ on jo luotu. Kaaviossa aika etenee alaspäin, eli alussa olemassa olevat laatikot _main_, _rekisteri_ ja _pankki_ on piirretty kaavion yläosaan.

Toiminta alkaa siitä kun pääohjelma eli main luo hebkilön nimeltä arto. Seuraavaksi main kutsuu rekisterin metodia _lisaa_ ja antaa parametriksi luodun henkilöolion.

Vastaava toistuu kun main luo uuden henkilön ja lisää sen rekisteriin.

Seuraavana toimenpiteenä main kasvattaa arton palkkaa kutsumalla rekisterin metodia _asetaPalkka_.  Tämä saa aikaan sen, että _rekisteri_ kutsuu _arto_-olion metodia _setPalkka_. Rekisterin viivaan on merkitty paksunnus, joka korostaa, että sen metodin on kutsuttu.

Viimeinen ja monimutkaisin toiminnoista käynnistyy kun main kutsuu rekisterin metodia _suoritaPalkanmaksu_. Rekisteri kysyy ensin arton tilinumeroa ja palkkaa ja kutsuu paluuarvoina olevilla tiedoilla pankin metodia _maksaPalkka_ ja sama toistuu sasun kohdalla.

Sekvenssikkaaviot eivät ole optimaalinen tapa ohjelman suorituslogiikan kuvaamiseen. Ne sopivat jossain määrin olio-ohjelmien toiminnan kuvaamiseen, mutta esim. funktionaalisella tyylillä tehtyjen ohjelmien kuvaamisessa ne ovat varsin heikkoja.

Tietynlaisten tilanteiden kuvaamiseen ohjelmoinnin perusteissakin käsitellyt [vuokaaviot](https://materiaalit.github.io/ohjelmointi-18/part2/) voivat sopia paremmin.

Voit halutessasi lukea lisää kurssin vanhan version [materiaalista](https://github.com/mluukkai/OTM2016/blob/master/luennot/luento5.pdf).

# Lisää ohjelmiston suunnittelusta

### Todo-sovelluksen suunnittelu

Todo-sovelluksen arkkitehtuurikuvaus
[täällä]https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/arkkitehtuuri.md).


Ohjelmiston {\em arkkitehtuurilla} tarkoitetaan\footnote{Arkkitehtuurin käsite on laaja ja hieman monisyisempi kun tässä esitetty. Arkkitehtuurin käsitettä tarkennetaan 2. vuoden kevään kurssilla Ohjelmistotuotanto sekä Ohjelmistojärjestelmien linjan syventävissä opinnoissa kurssilla Ohjelmistoarkkitehtuurit.} karkeasti ottaen ohjelmiston korkean tason rakennetta, sen jakautumista erillisiin komponentteihin ja näiden rakennekomponenttien suhteita. 

Komponentilla tässä tarkoitetaan yleensä kokoelmaa toisiinsa loogisesti liittyviä olioita, jotka suorittavat jotain tiettyä tehtävää ohjelmassa, esim. käyttöliittymän voitaisiin ajatella olevan yksi komponentti. Toisaalta ison komponentin voidaan ajatella koostuvan useista alikomponenteista, esim. sovelluslogiikkakomponetti voisi sisältää komponentin, joka huolehtii sovelluksen alustamisesta ja yhden komponentin kutakin järjestelmän toimintokokonaisuutta varten. Toisaalta komponenttijako voi perustua myös tietosisältöihin, esim. kirjastojärjestelmässä voisi olla omat komponentit lainaajia, lainoja ja kirjakokoelmaa varten.

Jos ajatellaan pelkkää ohjelman jakautumista komponenteiksi, puhutaan {\em loogisesta arkkitehtuurista}. Looginen arkkitehtuuri ei ota kantaa siihen miten eri komponentit sijoitellaan, eli toimiiko esim. käyttöliittymä samassa koneessa kuin sovelluksen käyttämä tietokanta.

Sovelluksen loogisen arkkitehtuurin kuvaamiseen sopivat UML:n {\em pakkauskaaviot} (engl. package diagram). Kuvassa \ref{fig:kirja6} esitetään kirjastojärjestelmän karkean tason arkkitehtuuria\footnote{Puhuttaessa arkkitehtuurista, tarkoitetaan tässä luvussa usein nimenomaan loogista arkkitehtuuria eli ei oteta kantaa komponenttien sijoittelusta fyysisille tietokoneille.} vastaava UML:n pakkauskaavio.

\begin{figure}[htbp]
    \centering
    \includegraphics[width=25mm]{kirja6}
    \caption{Kirjastojärjestelmän looginen arkkitehtuuri}
    \label{fig:kirja6} 
\end{figure}

Kirjastojärjestelmän rakenne noudattaa ns. {\em kerrosarkkitehtuuria} (engl. layered architecture), joka on yksi hyvin tunnettu {\em arkkitehtuurinen malli} (engl. architecture pattern), eli periaate, jonka mukaan tietynlaisia ohjelmia kannattaa pyrkiä rakentamaan. Kerros on kokoelma toisiinsa liittyviä olioita tai alikomponentteja, jotka muodostavat esim. toiminnallisuuden suhteen loogisen kokonaisuuden ohjelmistosta. Kerrosarkkitehtuurissa on pyrkimyksenä järjestellä komponentit siten, että {\em ylempänä oleva kerros käyttää ainoastaan alempana olevien kerroksien tarjoamia palveluita}. Ylimpänä kerroksista on käyttöliittymäkerros, sen alapuolella sovelluslogiikka ja alimpana tallennuspalveluiden kerros, eli esimerkiksi tietokanta, jonne sovelluksen olioita voidaan tarvittaessa tallentaa.

Pakkauskaaviossa yksi komponentti kuvataan {\em pakkaussymbolilla}, eli laatikolla, jonka vasemmassa ylänurkassa on pieni laatikko. Pakkauksen nimi on joko kuvan \ref{fig:kirja6} tapaan keskellä pakkaussymbolia tai ylänurkan pienemmässä laatikossa. \label{sec:pakkaus}

Pakkausten välillä olevat riippuvuudet ilmaistaan katkoviivalla, joka suuntautuu pakkaukseen, johon riippuvuus kohdistuu. Kerrosarkkitehtuurissa siis on pyrkimyksenä, että riippuvuuksia on ainoastaan alapuolella oleviin kerroksiin. Kirjastojärjestelmän käyttöliittymäkerros siis riippuu sovelluslogiikkakerroksesta. Riippuvuus tarkoittaa käytännössä sitä,  että käyttöliittymän oliot kutsuvat sovelluslogiikan olioiden metodeja. Sovelluslogiikkakerros taas on riippuvainen tallennuspavelukerroksesta.

Pakkauksen sisältö on mahdollista piirtää pakkaussymbolin sisään, kuten kuvassa \ref{fig:kirja7} on tehty.  Kuva \ref{fig:kirja7}  esittää kirjastojärjestelmän arkkitehtuurin hieman tarkemman version. Pakkauksen sisällä voi olla muutakin kuin alipakkauksia, kuten esim. luokkia.

\begin{figure}[htbp]
    \centering
    \includegraphics[width=100mm]{kirja7}
    \caption{Kirjastojärjestelmän looginen arkkitehtuuri tarkemmin}
    \label{fig:kirja7} 
\end{figure} 

Sovelluslogiikkapakkauksen sisään on piirretty osa sovelluslogiikan luokista. Kuvassa ei siis näytetä kaikkia luokkia ja se tulee tarkentumaan myöhemmin. Käyttöliittymäpakkaus koostuu kahdesta alipakkauksesta, joista toinen on graafinen käyttöliittymä ja toinen testauskäyttöön tarkoitettu tekstipohjainen konsolikäyttöliittymä. Käyttöliittymäpakkaus on riippuvainen sovelluslogiikkapakkauksesta ja sovelluslogiikkapakkaus tallennuspalvelupakkauksesta. Kuvasta ilmenee myös se, että konsolikäyttöliittymän toteuttava pakkaus käyttää suoraan tallennuspalvelupakkauksen loki-tiedostoon kirjoittamisen toteuttavaa alipakkausta. Kysessä on alipakkauksien keskinäinen riippuvuus, graafisen käyttöliittymän toteuttava pakkaus ei siis ole riippuvainen tallennuspalveluista.

Pakkausten yhteydessä voidaan käyttää nimeämiskäytäntöä, jossa komponentin (esim. alipakkauksen) nimi on useampiosainen, esim. {\em Kayttoliittyma::Konsoli} viittaa pakkauksen Kayttoliittyma sisällä olevaan Konsoli-nimiseen komponenttiin.

UML:n pakkaussymbolilla voidaan ryhmitellä mitä tahansa UML-komponentteja, eli pakkauksia, luokkia, olioita, käyttötapauksia, \ldots. Kirjastojärjestelmän käyttötapaukset voitaisiin esim. jakaa ylläpidon helpottamiseksi tai dokumentoinnin selkeyttämiseksi neljään eri pakkaukseen kuten kuvassa \ref{fig:kirja1b}, jossa ainoastaan kahden pakkauksen sisältö on näkyvillä. 

\begin{figure}[htbp]
    \centering
    \includegraphics[width=100mm]{kirja1b}
    \caption{Kirjastojärjestelmän käyttötapausten jakautuminen pakkauksiin}
    \label{fig:kirja1b} 
\end{figure} 

Jos pakkauksessa on paljon sisältöä, voi sisällön näyttäminen piirtämällä sisältyvät komponentit pakkauksen sisäpuolelle olla joskus ongelmallista. Tällöin voidaan käyttää vaihtoehtoista tapaa, jossa pakkaukseen sisältyvät komponentit piirretään pakkauksen ulkopuolelle mutta liitetään ne sisältävään
pakkaukseen käyttämällä kuvassa \ref{fig:kirja7b} esiteltyä merkintää, sisältyvyysrelaatiota. Kuvassa \ref{fig:kirja7b} on esitetty kirjastojärjestelmän arkkitehtuuri yleistasolla. Tallennuspalvelupakkauksen sisältö on näytetty käyttäen sisältyvyysrelaatiota.

\begin{figure}[htbp]
    \centering
    \includegraphics[width=50mm]{kirja7b}
    \caption{Vaihtoehtoinen tapa näyttää pakkauksen sisältö}
    \label{fig:kirja7b} 
\end{figure} 


\subsubsection{Kerrosarkkitehtuurin etuja} \label{sec:kerrosark}

Kerrosarkkitehtuurilla on monia etuja. Kerroksittaisuus helpottaa ylläpitoa, sillä jos tietyn kerroksen palvelurajapintaan (eli muille kerroksille näkyvään osaan) tehdään muutoksia, aiheuttavat muutokset ylläpitotoimenpiteitä ainoastaan ylemmän kerroksen riippuvuuksia omaavissa pakkauksessa. Esim. käyttöliittymän muutokset eivät vaikuta sovelluslogiikkaan tai tallennuspalveluihin.
%\footnote{Palaamme myöhemmin tarkemmin siihen, miten sovelluslogiikka saadaan riippumattomaksi käyttöliittymästä.} 
Sovelluslogiikan riippumattomuus käyttöliittymästä helpottaa ohjelman siirtämistä uusille alustoille, esim. toimimaan www-selaimen kautta. Alimpien kerroksien palveluja, kuten lokitiedostoon kirjoitusta tai tietokantayhteyksiä voidaan uusiokäyttää mahdollisesti myös muissa sovelluksissa. 

Myös kerrosten sisällä ohjelman loogisesti toisiinsa liittyvät komponentit kannattaa ryhmitellä omiksi pakkauksiksi\footnote{Parempi termi kuin pakkaus tälläisestä mahdollisimman itsenäisestä osajärjestelmästä olisi esim. komponentti, käytetään kuitenkin nyt termiä pakkaus koska komponenttijako kuvataan pakkauskaavioiden avulla. Kurssilla ohjelmistoarkkitehtuurit käsitellään UML:n komponenttikaavio, joka oikeastaan sopii pakkauskaaviota paremmin paremmin ohjelman arkkitehtuurin kuvaamiseen.}. Yksittäisistä pakkauksista kannattaa tehdä mahdollisimman yhtenäisiä toiminnallisuudeltaan, eli sellaisia, joiden osat kytkeytyvät tiiviisti toisiinsa ja palvelevat ainoastaan yhtä selkeästi eroteltua tehtäväkokonaisuutta. Samalla pyrkimyksenä on, että erilliset pakkaukset ovat mahdollisimman löyhästi toisiinsa kytkettyjä, eli pakkausten välisiä riippuvuuksia pyritään minimoimaan.

Ohjelman selkeä jakautuminen mahdollisimman riippumattomiin pakkauksiin eristää koodiin ja suunnitelmaan tehtävien muutosten vaikutukset mahdollisimman pienelle alueelle, eli ainoastaan riippuvuuden omaaviin pakkauksiin. Tämä helpottaa ohjelman ylläpitoa ja tekee sen laajentamisen helpommaksi. Selkeä jakautuminen pakkauksiin myös helpottaa työn jakamista suunnittelu- ja ohjelmointivaiheessa. 

Pelkkä kerroksittaisuus ei tee ohjelman arkkitehtuurista automaattisesti hyvää. Kuvassa \ref{fig:kirja8} tilanne, missä kerroksen $n+1$ kolmella alipaketilla on kullakin paljon riippuvuuksia kerroksen $n$ sisäisiin komponenttiin (tässä esimerkissä yksittäisiä luokkia). Esim. muutos kerroksen $n$ luokkaan 1 aiheuttaa nyt muutoksen hyvin moneen ylemmän kerroksen pakettiin. 

\begin{figure}[htbp]
    \centering
    \includegraphics[width=70mm]{kirja8}
    \caption{Kerroksella ei selkeää rajapintaa}
    \label{fig:kirja8} 
\end{figure} 

Mahdollinen ratkaisu ongelmaan on määritellä kerrosten välille selkeä {\em rajapinta}. Yksi tapa toteuttaa rajapinta on luoda kerroksen sisälle erillinen rajapintaolio, jonka kautta ulkoiset yhteydet tapahtuvat. Tätä periaatetta sanotaan  {\em fasaadimalliksi} (engl. Facade pattern). Kuvassa \ref{fig:kirja9} on luotu rajapintaolio kerrokselle $n$. Kaikki kommunikointi kerroksen kanssa tapahtuu rajapinnan kautta, eli ylemmän kerroksen riippuvuudet kohdistuvat ainoastaan rajapintaolioon. Nyt muutos esim. luokkaan 1 ei vaikuta kerroksen $n+1$ komponentteihin millään tavalla. Ainoat muutokset on tehtävä rajapintaolion sisäiseen toteutukseen.

\begin{figure}[htbp]
    \centering
    \includegraphics[width=70mm]{kirja9}
    \caption{Kerroksella hyvin määritelty rajapinta}
    \label{fig:kirja9} 
\end{figure} 

Kerrosarkkitehtuurin lisäksi on olemassa monia erilaisia arkkitehtuurimalleja eli hyväksi havaittuja tapoja jakaa järjestelmä kokonaisuuksiin, ks. esim \cite{arch}.

\subsubsection{Sovelluslogiikan ja Käyttöliittymän erottaminen} 
\label{sec:MVC}

Ennen oliosuunnitteluun siirtymistä on syytä vielä nostaa esille yksi kerrosarkkitehtuuriin liittyvä tärkeä seikka. Kerrosarkkitehtuurin ylimpänä kerroksena on yleensä käyttöliittymä. Yleensä pidetään järkevänä, että ohjelman sovelluslogiikka on täysin erotettu käyttöliittymästä. Käytännössä tämä tarkoittaa kahta asiaa:

\begin{itemize} \addtolength{\itemsep}{-0.5\baselineskip}
\item Sovelluksen palveluja toteuttavilla olioilla (mitkä suunnitellaan seuraavassa luvussa) ei ole suoraa yhteyttä käyttöliittymän olioihin, joita ovat esim. Java-ohjelmissa Swing-komponentit, kuten menut, painikkeet ja tekstikentät. Eli sovelluslogiikan oliot eivät esim. suoraan kirjoita mitään ruudulle.
\item Käyttöliittymän toteuttavat oliot eivät sisällä ollenkaan ohjelman sovelluslogiikkaa. Käyttöliittymäoliot ainoastaan piirtävät käyttöliittymäkomponentit ruudulle ja välittävät käyttäjän komennot eteenpäin sovelluslogiikalle.  
\end{itemize}

Käytännössä erottelu tehdään liittämällä käyttöliittymän ja sovellusalueen olioiden väliin erillisiä komponentteja, jotka koordinoivat käyttäjän komentojen aiheuttamien toimenpiteiden suoritusta sovelluslogiikassa. Erottelun pohjana on Ivar Jacobsonin \cite{Objectory} kehittämä idea oliotyyppien jaottelusta kolmeen osaan, {\em rajapintaolioihin, ohjausolioihin} ja {\em sisältöolioihin}. Käyttöliittymän (eli rajapintaolioiden) ja sovelluslogiikan (eli sisältöolioiden) yhdistävät {\em ohjausoliot} (engl. control objects). Käyttöliittymä ei siis ole suoraan yhteydessä sovelluslogiikkaan luokkiin, vaan ainoastaan välittää käyttäjien komentoja ohjausolioille, jotka huolehtivat sovelluslogiikan olioiden hyödyntämisestä. Seuraavassa luvussa esiteltävä Larmanin \cite{Larman} {\em ohjausperiaate} on hyvin lähellä Jacobsonin ideaa\footnote{Sovelluslogiikan ja käyttöliittymien erottelun yhteydessä puhutaan usein MVC-mallista \cite{arch}. MVC:tä tunteville tarkennettakoon, että Jacobsonin ja Larmanin ohjausoliot eivät ole tarkalleen ottaen aivan sama asia kuin MVC-mallin kontrolleri, ainakaan siinä mielessä kun MVC:tä ajatellaan esim. Javalla tapahtuvan käyttöliittymäohjelmoinnin yhteydessä \cite{JavaEE}. Javan kontrolleri on Jacobsonin ajattelussa rajapintaolio. Koska MVC-mallin mielekäs käsittely vaatii käyttöliittymäohjelmoinnin tuntemista, tutustutaan periaatteeseen vasta myöhemmillä kursseilla.}. 

%Käytännössä erottelu tapahtuu ns. {\em MVC (Model, View, Controller) -mallia hyödyntäen}. MVC-mallissa käyttöliittymän (View) ja sovelluslogiikan (Model) välille tulee ohjainkerros (Controller), joka huolehtii sovelluslogiikan palvelujen kutsumisesta. Käyttöliittymä ainoastaan {\em delegoi} eli siirtää käyttäjän tekemät komennot ohjaimelle, joka pyytää sovelluslogiikkaa suorittamaan vaadittavat toimenpiteet.

Sovellusalueen dataan tulevat muutokset tulee kyetä näyttämään myös käyttöliittymässä. Jyrkässä kerrosarkkitehtuuriperiaatteessahan palvelupyyntöjen pitäisi aina kulkea ylhäältä alaspäin, eli muuttuneiden tietojen välitys käyttöliittymälle aiheuttaa hankaluuksia kerroksellisuuden suhteen. Sovellusalueen tietojen muutosten välittäminen käyttöliittymälle hoidetaan oikeaoppisesti käyttäen ns. {\em tarkkailija}-periaatetta (engl. observer pattern)\footnote{Tarkkailijaperiaateessa käyttöliittymän komponentit rekisteröivät itsensä sovelluslogiikalle odottamaan päivityskäskyjä. Käyttöliittymän komponentit eivät kuitenkaan rekisteröi itseään suoraan vaan ainoastaan ns. tarkkailurajapinnan kautta. Sovelluslogiikka tunteekin ainoastaan joukon sitä tarkkailevia rajapintoja, konkreettisia käyttöliittymän komponentteja jotka toteuttavat tarkkailurajapinnat ei sovelluslogiikka tunne \cite{GOF}.}

Sovelluslogiikan erottaminen käyttöliittymästä mahdollistaa myös sen, että samasta sovellusalueen datasta voi olla olemassa useita erilaisia näkymiä yhtäaikaa. Eli sama data pystytään näyttämään eri tavoin käyttäjän tarpeista riippuen, esim. joko tekstuaalisessa muodossa tai graafisena diagrammina.

# Toteutukseen ja suunnitteluun liittyviä asioita

## Single responsibility -periaate

	\subsection{Single responsibility principle}
	
	\begin{frame}
		\simpleframetitle
		
		\begin{itemize}
			\item \textbf{Single responsibility} tarkoittaa karkeasti ottaen, että \textbf{oliolla tulee olla vain yksi vastuu} eli yksi asiakokonaisuus, mihin liittyvästä toiminnasta luokan oliot itse huolehtivat
			\item Robert C. Martin: \\ \textit{”A class should have only one reason to change.”}
			\pause
			\item Todo-sovelluksen suunnittelussa periaatetta on noudatettu suhteellisen hyvin
			 \begin{itemize}
			 	\item käyttölittymästä on eristetty sovelluslogiikka kokonaan
			 	\item käyttäjän interaktioon reagoiminen on eriytetty tapahtumankäsittelijöille
			 	\item sovelluslogiikan suorittamista koordinoi oma luokka
			 	\item käyttäjä ja tehtävät on talletettu omiin luokkiinsa
			 	\item todo-apin kanssa kommunikoinnin hoitavat omat luokkansa jotka vielä jaettu kahteen vastuualueeseen
			 \end{itemize}	
		\end{itemize}
	\end{frame}
	
	\subsection{Program to an interface, not to an Implementation}
	
	\begin{frame}
		\simpleframetitle
		
		\begin{itemize}
			\item "\textbf{Program to an interface, not to an Implementation}", eli \ldots ohjelmoi käyttämällä rajapintoja äläkä konkreettisia implementaatioita
			\item Laajennettavuuden kannalta ei ole hyvä idea olla riippuvainen konkreettisista luokista, sillä ne saattavat muuttua
			\item Parempi on tuntea vain rajapintoja (tai abstrakteja luokkia) ja olla tietämätön siitä mitä rajapinnan takana on
			\item Tämä mahdollistaa myös rajapinnan takana olevan luokan korvaamisen kokonaan uudella luokalla
		\end{itemize}
	\end{frame}

	\subsection{Riippuvuuksien minimointi}
	
	\begin{frame}
		\simpleframetitle
		
		\begin{itemize}
			\item \textbf{Minimoi riippuvuudet}, eli älä tee \textit{spagettikoodia}, jossa kaikki oliot tuntevat toisensa
			\item Pyri eliminoimaan riippuvuudet siten, että luokat tuntevat mahdollisimman vähän muita luokkia, ja mielellään nekin vain rajapintojen kautta 
		\end{itemize}
		\pause
		~ 
		\begin{itemize}
			\item Kerrosarkkitehtuuri tähtää osaltaan riippuvuuksien eliminointiin
			\item Katsomme ensi viikolla konkreettisesti sitä, miten kerrosten riippuvuuksien hallinta hoidetaan sovelluksessamme siten, että \textbf{turhien riippuvuuksien} eliminoimisen ansiosta saamme sovelluksesta helposti testattavan
		\end{itemize}		
	\end{frame}

## refaktorointi

# lisää testauksesta

### Todo-sovelluksen testaus

Todo-sovelluksen testausdokumentti
[täällä]https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/testaus.md).
