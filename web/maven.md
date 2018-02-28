# KESKEN

# Ohjeita maveniin

## projektin luominen

Ohje maven-muotoisen projektin luomiseen NetBeansilla [täällä](https://github.com/mluukkai/otm-2018/blob/master/web/tyon_aloitus.md#maven-projektin-luominen)

Vaikka käyttäisit JavaFX:ää, kannattaa projektia varten silti luoda ohjeen mukaan "normaali" maven-projekti.

## Testit ja Testikattavuus

Lisää tiedostoon _pom.xml_ seuraavat

```xml
<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>
</dependencies>
<build>
    <plugins>
        <plugin>
            <groupId>org.jacoco</groupId>
            <artifactId>jacoco-maven-plugin</artifactId>
            <version>0.8.0</version>
            <executions>
                <execution>
                    <id>default-prepare-agent</id>
                    <goals>
                        <goal>prepare-agent</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>  
    </plugins>
</build>
```

Huomaa, että määrittelyt on lisättävä _Project_-tagien sisälle:

<img src="https://raw.githubusercontent.com/mluukkai/otm-2018/master/web/images/m-1.png" width="700">

Voit nyt suorittaa testauskattavuuden mittaamisen komennolla

```xml
mvn test jacoco:report
```

Katso lisää [viikon 2 laskareista](https://github.com/mluukkai/otm-2018/blob/master/tehtavat/viikko2.md#3-testauskattavuus).

### pakkausten exkludaus

## maven-komentojen suorittaminen NetBeansista

## Checkstyle

## JavaDoc

## jarin generointi

## hieman lisää mavenia

* Luo NetBeansilla maven-muotoinen projekti, jonka sijoitat tehtävien alussa tekemäsi _repositoriosi juureen_.
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
* NetBeans onkin lisännyt automaattisesti hakemiston ignoroitavksi
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

Nyt koodi on kenen tahansa ladattavissa menemällä GitHub-repositorioosi, ja klikkaamalla repositoriosivusi kohtaa "1 release" ja suoritettavissa komennolla <code>java -jar tiedostonnimi.jar</code> olettaen että koneelle on asennettu Javan versio 1.8

Tämän kurssin osalta git-harjoittelumme loppuu tähän. Nyt opittu riittää hyvin yhden ihmisen käyttöön, esim. ohjelmoinnin harjoitustyön yhteydessä.

Gitissä on runsaasti hyödyllisiä ominaisuuksia joihin emme vielä tutustuneet. 
