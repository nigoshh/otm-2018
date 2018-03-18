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

Pisteet (yht 23) jakautuvat seuraavasti
- käyttöliittymä 4p
  - 0p yksinkertainen tekstikäyttöliittymä
  - 1-2p monimutkainen tekstikäyttöliittymä
  - 2-3p yksinkertainen graafinen käyttöliittymä
  - 4p laaja graafinen käyttöliittymä
- tiedon pysyväistallennusta 4p
  -	ei pysyväistallennusta
  - 1-2p	tiedosto 
  - 3-4p	tietokanta
  - 3-4p	internet
	- Pisteytys riippuu käsiteltävän tiedon monimutkaisuudesta
	- Täydet pisteet kussakin kategorioissa edellyttävät järkevien abstraktioiden, esim. DAO-suunnittelumallin käyttöä
- sovelluslogiikan kompleksisuus 3p
- ohjelman laajuus 5p
- ulkoisten kirjastojen hyödyntäminen 1p
- suorituskelpoinen jar-tiedosto  1p
- koodin laatu 6p
  - 5p hyvät abstraktiot (esim. Design patternien hyödynnys), hyvä luokkarakenne, helposti testattava ja laajennettava
  - 3p ei ilmeistä copypastea, ok luokkarakenne
  - +1p checkstylesäännöt kunnossa
  
## Testauksesta annettavat pisteet

Täysien pisteiden (5p) edellytys:
- Testattu kattavasti, rivi- ja haarautumakattavuus korkea
- Testaus riittävää sekä yksikkö- että integraatiotasolla
- Sovelluslogiikkaa testataan realistisilla skenaarioilla
- Riippuvuudet mockattu järkevästi
