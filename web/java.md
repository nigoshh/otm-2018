# KESKEN

# Muutamia toteutukseen liittyviä vihjeitä

## Sovelluksen käyttöliittymä

Voit siis tehdä sovelluksellesi tekstikäyttöliittymän tai graafisen käyttöliittymän. Tekstikäyttöliittymän tekeminen on toki useimmiten huomattavasti helpompaa, mutta se voi olla hieman tylsää ja graafisen käyttöliittymän tekemättömyys saattaa [vaikuttaa arvosanaan](https://github.com/mluukkai/otm-2018/blob/master/web/arvvosteluperusteet.md)

Pääasia on jokatapauksessa, että pyrit _eriyttämään mahdollisimman hyvin sovelluslogiikan käyttöliittymästä_. Käyttöliittymän roolin tulee siis olla ainoastaan käyttäjän kanssa tapahtuva interaktio, varsinaisen logiikan tulee tapahtua muissa oliossa. 

### Eräs malli tekstikäyttöliittymälle

Ohjelmoinnin jatkokurssin viikon 9 tehtävän [numerotiedustelu](https://materiaalit.github.io/ohjelmointi-s17/part9/) malliratkaisu tarjoaa erään kohtuullisen hyvän mallin teksikäyttöliittymälle.

Pääohjelma ei tee mitään muuta kuin luo ja käynnistää luokan _Numerotiedustelu_ instanssin:

```java
public class Paaohjelma {
 
    public static void main(String[] args) {
        Scanner lukija = new Scanner(System.in);
 
        Numerotiedustelu numerotiedustelu = new Numerotiedustelu(lukija);
        numerotiedustelu.kaynnista();
    }
}
```

_Numerotiedustelu_ on oikeastaan sovelluksen tekstikäyttöliittymä. Varsinainen sovelluslogiikka on luokan _NumeroJaOsoitepalvelu_ vastuulla. 

Osa luokan _Numerotiedustelu_ koodia seuraavassa:

```java
public class Numerotiedustelu {
 
    private Scanner lukija;
    private Map<String, String> komennot;
    private NumeroJaOsoitepalvelu palvelu;
 
    public Numerotiedustelu(Scanner lukija) {
        this.lukija = lukija;
        palvelu = new NumeroJaOsoitepalvelu();
 
        komennot = new TreeMap<>();
        
        komennot.put("x", "x lopeta");
        komennot.put("1", "1 lisää numero");
        komennot.put("2", "2 hae numerot");
        komennot.put("3", "3 hae puhelinnumeroa vastaava henkilö");
        komennot.put("4", "4 lisää osoite");
        komennot.put("5", "5 hae henkilön tiedot");
        komennot.put("6", "6 poista henkilön tiedot");
        komennot.put("7", "7 filtteröity listaus");
        komennot.put("x", "x lopeta");
    }
 
    public void kaynnista() {
        System.out.println("numerotiedustelu");
        tulostaOhje();
        while (true) {
            System.out.println();
            System.out.print("komento: ");
            String komento = lukija.nextLine();
            if (!komennot.keySet().contains(komento)) {
                System.out.println("virheellinen komento.");
                tulostaOhje();
            }
 
            if (komento.equals("x")) {
                break;
            } else if (komento.equals("1")) {
                lisaaNumero();
            } else if (komento.equals("2")) {
                haeNumerot();
            } else if (komento.equals("3")) {
                haeHenkilo();
            } else if (komento.equals("4")) {
                lisaaOsoite();
            } else if (komento.equals("5")) {
                haeTeidot();
            } else if (komento.equals("6")) {
                poistaHenkilo();
            } else if (komento.equals("7")) {
                listaus();
            }
 
        }
    }
 
    private void haeNumerot() {
        System.out.print("kenen: ");
        String nimi = lukija.nextLine();
        Collection<String> numerot = palvelu.haeNumerot(nimi);
        if (numerot.isEmpty()) {
            System.out.println("  ei löytynyt");
            return;
        }
 
        for (String numero : numerot) {
            System.out.println(" " + numero);
        }
    }
 
    private void lisaaNumero() {
        System.out.print("kenelle: ");
        String nimi = lukija.nextLine();
        System.out.print("numero: ");
        String numero = lukija.nextLine();
        palvelu.lisaaNumero(nimi, numero);
    }
 
    // lisää käyttöliittymäfunktioita...
}
```

Koodi tulostaa ruudulle komentojen nimet, kysyy käyttäjän syötettä ja suorittaa halutun toimenpiteen:

<img src="https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/j-1.png" width="700">

Koodi haarautuu käyttäjän valinnan mukaan if:issä valitun toimenpiteen suorittavaan metodiin. Esim. jos valinta on 1, suoritetaan tiedot luetteloon lisäävä metodi:

```java
private void lisaaNumero() {
    System.out.print("kenelle: ");
    String nimi = lukija.nextLine();
    System.out.print("numero: ");
    String numero = lukija.nextLine();
    palvelu.lisaaNumero(nimi, numero);
}
```

Metodi ei kuitenkaan itse tiedä puhelinluettelosta mitään, luettelointitehtäviä eli *sovelluslogiikkaa* hoitaa muuttujaan _palvelu_ talletettu _NumeroJaOsoitepalvelu_-olio, jonka metodia _lisaaNumero_ käyttöliittymä kutsuu käyttäjän antama syöte parametrina.

Koska sovelluslogiikka tapahtuu kokonaan erillään käyttöliittymästä, voidaan sen toimivuus
 testata helposti JUnitin avulla automatisoidusti.

## Riippuvuuden injektointi

Mallivastauksen koodi ei kuitenkaan ole ihan optimaalinen ja sitä saa parannettua helposti pienellä kikalla. Muutetaan _Numerotiedustelu_ muotoon

```java
public class Numerotiedustelu {
 
    private Scanner lukija;
    private Map<String, String> komennot;
    private NumeroJaOsoitepalvelu palvelu;
 
    public Numerotiedustelu(Scanner lukija, NumeroJaOsoitepalvelu palvelu) {
        this.lukija = lukija;
        this.palvelu = palvelu;
        palvelu = new NumeroJaOsoitepalvelu();
 
        komennot = new TreeMap<>();
        
        komennot.put("x", "x lopeta");
        // ...
    }

    // ...
}    
```

Pääohjelmaa täytyy nyt muuttaa seuraavasti:

```java
public class Paaohjelma {
 
    public static void main(String[] args) {
        Scanner lukija = new Scanner(System.in);
        NumeroJaOsoitepalvelu palvelu = new NumeroJaOsoitepalvelu();
 
        Numerotiedustelu numerotiedustelu = new Numerotiedustelu(lukija, palvelu);
        numerotiedustelu.kaynnista();
    }
}
```

Ero on hyvin pieni, nyt sovelluslogiikasta huolehtiva _NumeroJaOsoitepalvelu_-olio luodaan pääohjelmassa ja annetaan käyttöliittymänä toimivalle _Numerotiedustelu_-oliolle konstruktorin parametrina.

Tästä tekniikasta käytetään nimitystä [riippuvuuden injektointi](https://github.com/mluukkai/otm-2018/blob/master/web/materiaali.md#riippuvuuksien-injektointi), sillä  _NumeroJaOsoitepalvelu_-olio on _Numerotiedustelu_-olion riippuvuus joka tässä myöhemmässä versiossa injetoidaan konstruktoriparametrin avulla riippuvuutta tarvitsevalle oliolle. Aiemmassa versiossahan numerotiedustelu loi riippuvuuden itse.

Riippuvuuksien injektoinnista on monia etuja, eräs näistä on laajennettavuus.

Voisimme luoda uuden parannellun version numero- ja osoitepalvelusta perinnän avulla:

```java
public class ParanneltuNumeroJaOsoitepalvelu extends NumeroJaOsoitepalvelu {
  // ...
}
```

Laajennettu palvelu voisi käyttää vanhaa käyttöliittymää sellaisenaan:

```java
public class Paaohjelma {
 
    public static void main(String[] args) {
        Scanner lukija = new Scanner(System.in);
        ParanneltuNumeroJaOsoitepalvelu palvelu = new ParanneltuNumeroJaOsoitepalvelu();
 
        Numerotiedustelu numerotiedustelu = new Numerotiedustelu(lukija, palvelu);
        numerotiedustelu.kaynnista();
    }
}
```

Toinen etu merkittävä etu on testauksen helpottaminen. Se onkin syynä sille, miksi _Scanner_ injektoidaan _Numerotiedustelu_-oliolle.

Testit toimivat seuraavaan tyyliin:

```java
public class NumerotiedusteluTest {
 
    public void numeronLisays() 
        Scanner lukija = new TestausSkanner(
          "1",
          "Arto Hellas",
          "040-123456",
          "x"
        );

        NumeroJaOsoitepalvelu palvelu = new NumeroJaOsoitepalvelu();
 
        Numerotiedustelu numerotiedustelu = new Numerotiedustelu(lukija, palvelu);
        numerotiedustelu.kaynnista();

        // varmista assert-lauseella että ohjelman tulostus oli se halutun kaltainen
    }
}
```

Eli testi antaa _Numerotiedustelu_-oliolle simuloidun syötteen, joka toimii numerotiedustelun kannalta normaalin Scannerin tavoin. Suorituksen jälkeen testi varmistaa, että ohjelman tulostus on halutun kaltainen. 

### Java FX

Graafisen käyttöliittymän toteuttamiseen kannattaa oletusarvoisesti käyttää JavaFX:ää, jonka käytön perusteet esitellään [Ohjelmoinnin jatkokurssilla](https://materiaalit.github.io/ohjelmointi-s17/part11/)

Myös graafista käyttöliittymää käytettäessä tulee periaatteen olla se, että käyttöliittymän koodi ei sisällä sovelluslogiikkaa.

Mallia voi ottaa esimerkiksi kurssin referenssisovelluksen [TodoApp:in](https://github.com/mluukkai/OtmTodoApp/) koodista ja [arkkitehtuurikuvauksesta](https://github.com/mluukkai/OtmTodoApp/blob/master/dokumentaatio/arkkitehtuuri.md)

### Sovelluksen alustaminen ja sulkeminen

Kuten jatkokurssin materiaalissa kerrotaan, JavaFX-sovelluksen käyttöliittymästä vastaava pääluokka on peritty luokasta _Application_.

_main_-metodi ei yleensä tee mitään muuta kuin kutsuu metodia _launch_ joka taas saa aikaan sen, että pääluokasta luodaan instanssi ja instanssin metodeita _init_ ja _start_ kutsutaan.

Metodi _start_ on pakko toteuttaa ja sen suorituksen aikana muodostetaan käyttöliittymä. Metodin _init_ toteutus on vapaaehtoinen ja se on erinomainen paikka alustaa projektin riippuvuudet sillä metodi suoritetaan ennen start:ia. Teknisten rajoitteiden takia JavaFX-sovelluksille on hankalaa antaa riippuvuuksia samaan tapaan konstruktori-injektiolla kuin mitä aiemmassa esimerkissä teimme.

Seuraavassa ote Todo-sovelluksen käyttöliittymän koodista:

```java
public class TodoUi extends Application {
    // sovelluslogiikka  
    private TodoService todoService;
    
    @Override
    public void init() {
        FileUserDao userDao = new FileUserDao("users.txt");
        FileTodoDao todoDao = new FileTodoDao("todos.txt", userDao);
        // alustetaan sovelluslogiikka 
        todoService = new TodoService(todoDao, userDao);
    }

    @Override
    public void start(Stage primaryStage) {   
      // muodosta käyttöliittymä täällä
  
      Button createTodo = new Button("create");
      // käyttöliittymä kutsuu todoService-olioa hoitamaan sovelluslogiikkaan liittyvät toimet
      createTodo.setOnAction(e->{
          todoService.createTodo(newTodoInput.getText());
          newTodoInput.setText("");       
          redrawTodolist();
      });

      primaryStage.setOnCloseRequest(e->{
        System.out.println("sovellus on aikeissa sulkeutua");
        if (enHaluaEttaSovellusSulkeutuu) {
          e.consume();   
        }
      });
    }    

    @Override
    public void stop() {
      // tee lopetustoimenpiteet täällä
      System.out.println("sovellus sulkeutuu");
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```

Koodi havainnollistaa myös tapaa, miten lambda-funktiona määritelty _createTodo_-napin tapahtumankäsittelijä kutsuu sovelluslogiikan metodia _todoService.createTodo_. 

Koodissa on myös metodi [stop](https://docs.oracle.com/javase/8/javafx/api/javafx/application/Application.html#stop--) joka suoritetaan aina viimeisenä ennen sovelluksen sulkeutumista. Metodissa voidaan suorittaa tarvittavia lopetustoimia, esim. tiedostojen tallentamista.

Metodin _start_ lopuun on rekisteröity tapahtumankuuntelija joka suoritetaan juuri ennen sovelluksen sulkemista. If-haara demonstroi miten sulkemisen voi vielä estää tapahtumankuuntelijassa. 

### JavaFX-aiheisia linkkejä

Ohjelmoinnin jatkokurssilla tehdään JavaFX:n ainoastaan matala pintaraapaisu, jatkokurssin materiaali kannattaa kuitenkin ehdottomasti kerrata jos olet aikeissa käyttää JavaFX:ää. 

Jos käyttöliittymäsi on vähänkin epätriviaali, joudut suurella todennäköisyydellä etsimään itse lisää tietoa. Omatoimisen tiedonhaun harjoittelu onkin tämän kurssin eräs tärkeimmistä oppimistavoitteista. Seuraavassa muutamia linkkejä auttamaan alkuunpääsemistä. Jos löydät internetistä hyvää materiaalia, tee sivulle [pull request](https://github.com/mluukkai/otm-2018/blob/master/web/materiaali.md#kirjoitusvirheitä-materiaalissa)

-

### Scenebuilder

## tietojen talletus

### DAO

### injektoi daot...