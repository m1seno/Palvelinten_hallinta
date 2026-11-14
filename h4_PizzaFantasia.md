# Pizza Fantasia
Harjoitukset on tehty kotitoimistossa Kaarinassa. Koneena oli Tuxedo InfinityBook Pro AMD Gen10. Käyttöjärjestelmän toimi Parrot Security 7.4 (echo) x86_64.  
Harjoituksessa seurataan Teron kotisivujen (Karvinen 2026) tehtävänantoa.
## x) Lue ja tiivistä.
### 4.12.1 Size and Complexity of Some DSLs (Karvinen 2024, 112)
- Kappaleessa vertaillaan Saltin ja Puppetin DSL-kieliä (Domain Specific Language).
##### Salt
- Saltin DSL-kielessä on 510 tilafunktiota ja sen dokumentaatio on yli 20 000 riviä pitkä.
- Jinja2 malleja käytetään generoimaan YAML-koodia joka käännetään Python-koodiksi kun se ajetaan.
##### Puppet
- Puppet sisältää oletuksena 113 funktiota. Sen rakenne ei vastaa tyypillisiä ohjelmiontikieliä kuten C, Go tai Python.
- Tyypillisessä ohjelmointikielessä käytetään funktioita, joilla määritellään useasti toistettavia toimintoja. Puppetissa sen sijaan käytetään omanlaisia virtuaalisia resursseja.


### 4.12.2 Use of DSL Functions in Case Configuration (Karvinen 2024, 112-115)
- Kappaleessa vertailtiin kahta tuontoympäristössä käytettyä konfiguraatiota.
- Vaikka konfiguraationhallintatyökalut sisältävät valtavan määrän funktioita ja sääntöjä, seuraavat monet konfiguraatiot samankaltaista kaavaa esim. package-file-service, jolla pystytetään demoneja.
- Taulukosta 36 (Mozilla Release Engineering Puppet Manifests) huomaa, että tietyt funktiot ja ohjausrakenteet toistuvat satoja kertoja, jolloin käyttäjän ei todellisuudessa tarvitse muistaa kuin kourallisen keskeisiä komentoja.
- Myös taulukosta 37 (United States Government Configuration Baseline) huomaa, että suurin osa käytettävistä funktioista ja ohjausrakenteista keskittyvät package-file-service, exec ja group konfiguraatioihin.

### 4.12.3.1 Dependencies Between Main Functions (Karvinen 2024, 115-117)
- Järjestelmän tulisi olla idempotentti, mikä tarkoittaa, että muutoksia ei tehdä turhaan, jos haluttu tila on jo saavutettu.
- Useat toiminnot perustuvat käyttöjärjestelmän omiin komentoihin, kuten esimerkiksi paketin, tiedoston, käyttäjän ja ryhmien hallinta.
- Suurin osa konfiguraatioista voidaan toteuttaa käyttämällä vain paria perustoimintoa (exec ja file).
- Ylläpitäjän kannattaa opetella tehtävän manuaalinen konfigurointi, jonka jälkeen sen automatisointi onnistuu samoja toimintoja hyödyntäen.
## a) Räpylä. Asenna itse valitsemasi demoni käsin. Jokin muu kuin tunnilla tai kotitehtävissä aiemmin asennettu, eli ei apache, ngninx eikä openssh-server. Kuten aina, testaa lopputulos.
## b) Automaatti. Automatisoi valitsemasi demonin asennus Ansiblella.
## c) Asetus. Muuta asetustiedostoa herralla (master, "control node") ja aja ansible uudestaan. Osoita, että asetukset tulivat käyttöön.
## d) Paikka remonttiin. Riko jotain asetuksia. Voit esimerkiksi poistaa demonin 'sudo apt-get purge foobar' (purge poistaa myös asetustiedostoja), poistaa asennuksen yhteydessä tulevan kansion (sudo rm -r /etc/foobar/ # vaarallista) tms. Ja sitten ajaa ansible-roolisi uudestaan ja todeta, että se korjaa tilanteen.
## e) Idempotentti. Osoita, että tilasi on idempotentti.
## Lähteet
Karvinen, T . 2026. Palvelinten Hallinta. Luettavissa: https://terokarvinen.com/palvelinten-hallinta/ Luettu: 6.11.2026.

Karvinen, T . 2024. Väitöskirja. University of Westminster. https://westminsterresearch.westminster.ac.uk/item/w7vvz/configuration-management-of-distributed-systems-over-unreliable-and-hostile-networks
