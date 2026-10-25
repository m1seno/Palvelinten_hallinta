# Hei Ansiblen Maailma
Harjoitukset on tehty kotitoimistossa Kaarinassa. Koneena oli Tuxedo InfinityBook Pro AMD Gen10. Käyttöjärjestelmän toimi Fedora Linux 44.  
Harjoituksessa seurataan Teron kotisivujen (Karvinen 2026) tehtävänantoa.
## Lue ja tiivistä
#### SSH public key - Login without password (Karvinen 2026)
- SSH mahdollistaa salatun etäyhteyden avaamisen mihin tahansa koneeseen, jonka ip-osoite tai domain-nimi on käyttäjän tiedossa.
- Yhteys avataan komennolla `<käyttäjä>@<host>`. Esim. `kayttaja@kayttaja.com` tai `kayttaja@85.123.123.123`.
- Salasanaton kirjautuminen edellyttää ssh-avainparien käyttöä. Avainparin saa luotua komennolla `ssh-keygen`. Oman julkisen avaimen voi kopioida kohdekoneelle komennolla `ssh-copy-id <host>`.

Oma huomio: Jotta salasanaton kirjautuminen onnistuu, on julkisen ssh-avaimen oltava kyseisen käyttäjän authorized_keys -kansiossa. Kun esimerkiksi luo uuden virtuaalipalvelimen, julkinen avain siirretään root-käyttäjän kotihakemistoon. Yhteys täytyy siis avata root-käyttäjällä, ennen kun voi luoda uuden käyttäjän koneelle.
#### Hello Ansible (Karvinen 2026)

## Lähteet
Karvinen, T. 2026. Palvelinten Hallinta. Luettavissa: https://terokarvinen.com/palvelinten-hallinta/ Luettu: 23.10.2026
Karvinen, T. 2026. SSH public key - Login without password. Luettavissa https://terokarvinen.com/ssh-public-key-login-without-password/ Luettu: 23.10.2026.
Karvinen, T. 2026. Hello Ansible. Luettavissa: https://terokarvinen.com/hello-ansible/. Luettu: 23.10.2026.
