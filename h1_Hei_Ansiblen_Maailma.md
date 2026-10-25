# Hei Ansiblen Maailma
Harjoitukset on tehty kotitoimistossa Kaarinassa. Koneena oli Tuxedo InfinityBook Pro AMD Gen10. Käyttöjärjestelmän toimi Fedora Linux 44.  
Harjoituksessa seurataan Teron kotisivujen (Karvinen 2026) tehtävänantoa.

## x) Lue ja tiivistä

#### SSH public key - Login without password (Karvinen 2026)
- SSH mahdollistaa salatun etäyhteyden avaamisen mihin tahansa koneeseen, jonka ip-osoite tai domain-nimi on käyttäjän tiedossa.
- Yhteys avataan komennolla `<käyttäjä>@<host>`. Esim. `kayttaja@kayttaja.com` tai `kayttaja@85.123.123.123`.
- Salasanaton kirjautuminen edellyttää ssh-avainparien käyttöä. Avainparin saa luotua komennolla `ssh-keygen`. Oman julkisen avaimen voi kopioida kohdekoneelle komennolla `ssh-copy-id <host>`.

Oma huomio: Jotta salasanaton kirjautuminen onnistuu, on julkisen ssh-avaimen oltava kyseisen käyttäjän authorized_keys -tiedostossa. Kun esimerkiksi luo uuden virtuaalipalvelimen, julkinen avain siirretään root-käyttäjän kotihakemistoon. Yhteys täytyy siis avata root-käyttäjällä, ennen kun voi luoda uuden käyttäjän koneelle.

#### Hello Ansible (Karvinen 2026)
- Ansible on hallintaohjelma, jolla voi konfiguroida useampia koneita keskitetysti. 
- Ansible käyttää ssh -protokollaa yhteyden muodostamiseen, joten ssh demoni pitäisi olla asennettuna kohdekoneeseen.
- 

## a) Paikallista. Asenna Debian 13 paikallisesti virtuaalikoneeseen. Voit käyttää esimerkiksi VirtualBoxia. (Tätä käytetään myös tuntiharjoituksiin. Jos raportoit tämän jo h0 yhteydessä, pelkkä linkki raporttiin riittää. Suppea raportointi tässä alakohdassa: mikäli ongelmia ei tullut, pelkkä luettelo tehdyistä valinnoista riittää. Jos ongelmia, yksityiskohtainen, toistettava raportti.)
Minulla on linux omassa läppärissäni, jolla tulen tekemään kaikki tämän kurssin tehtävät.
![](h1/fedora.png)

Olen myös aikaisemmin asentanut virtuaalikoneen, jolla voin tehdä testejä kurssin tehtävissä.
![](h1/parrot.png) 


## b) Sshecrets. Asenna SSH-demoni käsin ja testaa se kirjautumalla SSH:lla. (localhost kelpaa)
Aloitin käynnistämällä ssh demonin komennolla `sudo systemctl enable --now ssh`. Olin jo aikaisemmin asentanut ssh:n avainten generoimista varten.  
Tarkistin vielä, että demoni on käynnissä komennolla `sudo systemctl status ssh`. Kaikki vaikuttaisi olevan kunnossa.
![](h1/ssh-daemon.png)

Seuraava steppi oli siirtää oma julkinen avain authorized_keys tiedostoon. Tämä onnistui komennolla `ssh-copy-id <ip-osoite>`.
![](h1/ssh-copy-id.png)

Kävin tarkistamassa ja siellähän se on.
![](h1/public_key.png)

Testaamatta ei ole kuitenkaan valmis, joten avasin vielä etäyhteyden varmuuden vuoksi.
![](h1/parrotssh.png)

Vuokrasin myös virtuaalipalvelimen ja toistin edellämainitut toimenpiteet. Sain myös siihen yhteyden.
![](h1/debianssh.png)

Nyt minulla on siis keksi erillistä konetta mihin voin ajaa komentoja Ansiblella.

## c) Pubkey. Automatisoi ssh-kirjautuminen julkisella avaimella. (localhost kelpaa)


## d) Hei Ansible. Tee hei maailma ansiblella ja kokeile sitä SSH:n yli. (localhost kelpaa)


## e) Vapaaehtoinen bonus: kokeile Ansiblella jokin näista asetuksista: paketin asennus, asetustiedosto /etc/ alle, käynnistä jokin demoni, tee uusi käyttäjä. Tarvitset todennäköisesti sudoa, become: true.


## Lähteet
Karvinen, T. 2026. Palvelinten Hallinta. Luettavissa: https://terokarvinen.com/palvelinten-hallinta/ Luettu: 23.10.2026
Karvinen, T. 2026. SSH public key - Login without password. Luettavissa https://terokarvinen.com/ssh-public-key-login-without-password/ Luettu: 23.10.2026.
Karvinen, T. 2026. Hello Ansible. Luettavissa: https://terokarvinen.com/hello-ansible/. Luettu: 23.10.2026.
