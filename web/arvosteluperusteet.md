# Kurssin suorittaminen ja arvostelu

Kurssilla jaossa 60 pistettä. Pisteet jakautuvat alustavan suunnitelman mukaan seuraavasti

- Viikkodeadlinet 17p
- Koodikatselmointi 2p
- Dokumentaatio	10p   
  - Määrittely		
  - Arkkitehtuuri		
  - Käyttö/asennusohje	
  - Repositorio	
  - JavaDoc	
- Testaus	7p	
  - Testit			
  - Testidokumentti	
- Lopullinen ohjelma 24p
  - Featuret		
  - Koodin laatu 		

Arvosanaan 1 riittää 30 pistettä, arvosanaan 5 tarvitaan noin 55 pistettä.

Läpipääsyyn vaatimuksena on lisäksi vähintään 10 pistettä lopullisesta ohjelmasta.

## Lopullisesta ohjelmasta annettavat pisteet

Pisteet (yht 24) jakautuvat seuraavasti
- Käyttöliittymä 4p
  - 0p yksinkertainen tekstikäyttöliittymä
  - 1-2p monimutkainen tekstikäyttöliittymä
  - 2-3p yksinkertainen graafinen käyttöliittymä
  - 4p laaja graafinen käyttöliittymä
- Tiedon pysyväistallennusta 4p
  -	ei pysyväistallennusta
  - 1-2p	tiedosto 
  - 3-4p	tietokanta
  - 3-4p	internet (esim. google docs tai joku muu talletusratkaisu)
	- Pisteytys riippuu käsiteltävän tiedon monimutkaisuudesta
	- Täydet pisteet kussakin kategorioissa edellyttävät järkevien abstraktioiden, esim. DAO-suunnittelumallin käyttöä
- Sovelluslogiikan kompleksisuus 3p
- Ohjelman laajuus 5p
- Ulkoisten kirjastojen hyödyntäminen 1p
  - ks https://github.com/mluukkai/otm-2018/blob/master/web/maven.md#ulkoisten-kirjastojen-k%C3%A4ytt%C3%A4minen-mavenin-avulla
- Suorituskelpoinen jar-tiedosto  1p
- Koodin laatu 6p
  - 5p hyvät abstraktiot (esim. Design patternien hyödynnys), hyvä luokkarakenne, helposti testattava ja laajennettava
  - 3p ei ilmeistä copypastea, ok luokkarakenne
  - +1p checkstylesäännöt kunnossa  
  
Laajuus ja sovellusogiikan kompleksisuus
- Miten laaja on laaja?
- Kurssin [referenssisovellus](https://github.com/mluukkai/OtmTodoApp) olisi laajuudeltaan 3 pisteen arvoinen, sovelluslogiikaltaan se on aika suoraviivainen ja ansaitsisi vain yhden pisteen
- Eräs tapa laajentaa sovellusta ja lisätä sen kompleksisuutta on tehdä siitä parametrein konfiguroitava ja laajennettava, esim:
  - Sovelluksen käyttämän tietokantatiedoston nimi ei ole kirjoitettu koodiin vaan on käyttäjän määriteltävissä
  - Pelissä eri vaikueustasojen pelimaailmat eivät ole määritelty koodissa vaan luodaan erillisten tiedostojen perusteella
  - Pacmanissa hirviöiden määrä ei ole ohjelmakoodiin kovakoodattuvakio vaan valittavissa käyttöliittymästä
  - Konfiguroitavuus voidaan toteuttaa joko käyttöliittymän tai [konfiguraatiotiedostojen](https://github.com/mluukkai/otm-2018/blob/master/web/java.md#sovelluksen-konfiguraatiot) avulla
  
  
## Testauksesta annettavat pisteet

Täysien pisteiden (5p) edellytys:
- Testattu kattavasti, rivi- ja haarautumakattavuus korkea
- Testaus riittävää sekä yksikkö- että integraatiotasolla
- Sovelluslogiikkaa testataan realistisilla skenaarioilla
- Riippuvuudet mockattu järkevästi
