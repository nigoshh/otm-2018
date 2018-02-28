# KESKEN

# Muutamia toteutukseen liittyviä vihjeitä

## Sovelluksen käyttöliittymä

Voit siis tehdä sovelluksellesi tekstikäyttöliittymän tai graafisen käyttöliittymän. Tekstikäyttöliittymän tekeminen on toki useimmiten huomattavasti helpompaa, mutta se voi olla hieman tylsää ja graafisen käyttöliittymän tekemättömyys saattaa [vaikuttaa arvosanaan](https://github.com/mluukkai/otm-2018/blob/master/web/arvvosteluperusteet.md)

Pääasia on jokatapauksessa, että pyrit _eriyttämään mahdollisimman hyvin sovelluslogiikan käyttöliittymästä_. Käyttöliittymän roolin tulee siis olla ainoastaan käyttäjän kanssa tapahtuva interaktio, varsinaisen logiikan tulee tapahtua muissa oliossa. 

### Eräs malli tekstikäyttöliittymälle

Ohjelmoinnin jatkokurssin viikon 9 tehtävän [numerotiedustelu](https://materiaalit.github.io/ohjelmointi-s17/part9/) malliratkaisu tarjoaa erään kohtuullisen hyvän mallin teksikäyttöliittymälle.

```java
public class Paaohjelma {
 
    public static void main(String[] args) {
        Scanner lukija = new Scanner(System.in);
 
        Numerotiedustelu numerotiedustelu = new Numerotiedustelu(lukija);
        numerotiedustelu.kaynnista();
    }
}
```

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
 
    private void tulostaOhje() {
        System.out.println("käytettävissä olevat komennot: ");
        for (String komento : komennot.values()) {
            System.out.println(" " + komento);
        }
    }
 
    private void haeHenkilo() {
        System.out.print("numero: ");
        String numero = lukija.nextLine();
        String nimi = palvelu.haeNimi(numero);
        if (nimi == null) {
            System.out.println(" ei löytynyt");
            return;
        }
        System.out.println(" " + nimi);
    }
 
    private void lisaaOsoite() {
        System.out.print("kenelle: ");
        String nimi = lukija.nextLine();
        System.out.print("katu: ");
        String katu = lukija.nextLine();
        System.out.print("kaupunki: ");
        String kaupunki = lukija.nextLine();
        palvelu.lisaaOsoite(nimi, katu, kaupunki);
    }
 
    private void haeTeidot() {
        System.out.print("kenen: ");
        String nimi = lukija.nextLine();
        Henkilo henkilo = palvelu.haeNimenPerusteella(nimi);
        if (henkilo == null) {
            System.out.println("  ei löytynyt");
            return;
        }
 
        tulostaHenkilonTiedot(henkilo);
    }
 
    private void tulostaHenkilonTiedot(Henkilo henkilo) {
        tulostaOsoite(henkilo);
        tulostaPuhelinnumerot(henkilo);
    }
 
    private void tulostaOsoite(Henkilo henkilo) {
        if (henkilo.getKatu() == null || henkilo.getKaupunki() == null) {
            System.out.println("  osoite ei tiedossa");
            return;
        }
 
        System.out.println("  osoite: " + henkilo.getKatu() + " " + henkilo.getKaupunki());
    }
 
    private void tulostaPuhelinnumerot(Henkilo henkilo) {
        if (henkilo.getPuhelinnumerot().isEmpty()) {
            System.out.println("  ei puhelinta");
            return;
        }
 
        System.out.println("  puhelinnumerot:");
        for (String numero : henkilo.getPuhelinnumerot()) {
            System.out.println("   " + numero);
        }
    }
 
    private void poistaHenkilo() {
        System.out.print("kenet: ");
        String nimi = lukija.nextLine();
        palvelu.poista(nimi);
    }
 
    private void listaus() {
        System.out.print("hakusana (jos tyhjä, listataan kaikki): ");
        String hakusana = lukija.nextLine();
        Set<Henkilo> loytyi = palvelu.hae(hakusana);
        if (loytyi.isEmpty()) {
            System.out.println(" ei löytynyt");
            return;
        }
 
        for (Henkilo h : palvelu.hae(hakusana)) {
            System.out.println();
            System.out.println(" " + h.getNimi());
            tulostaHenkilonTiedot(h);
        }
    }
}
```java 


### Java FX

## tietojen talletus

### DAO