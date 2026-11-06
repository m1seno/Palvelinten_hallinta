# Demoni
Harjoitukset on tehty kotitoimistossa Kaarinassa. Koneena oli Tuxedo InfinityBook Pro AMD Gen10. Käyttöjärjestelmän toimi Fedora Linux 44.  
Harjoituksessa seurataan Teron kotisivujen (Karvinen 2026, 1) tehtävänantoa.

## x) Lue ja tiivistä
### Apache installed with Ansible – quick notes (Karvinen 2026, 2)
- Apache2-verkkopalvelimen asennus ja konfigurointi voidaan automatisoida Ansiblella.
- Palvelinten konfiguroinnissa käytetään package-file-service-mallia.
- Suurin osa demoneista ovat perus käyttöönotoltaan melko samanlaisia, joten niin on myöskin sen automatisointi automatisointi.
- Apache2-roolin hakemistorakenne koostuu tasks, files ja handlers -hakemistoista.
- notify ilmoittaa handlerille, että konfiguraatiotiedostoon on tehty muutoksia ja Apache pitää käynnistää uudelleen.

Oma havainto: Verkkosivuston tiedostot voidaan sijoittaa tavallisen käyttäjän kotihakemistoon, jolloin sivustoa voidaan muokata ilman sudo-oikeuksia.

### Handlers: running operations on change (Ansible Community Documentation)
- Handlerit ovat Ansible-tehtäviä, jotka suoritetaan vain silloin, kun jokin toinen tehtävä ilmoittaa tapahtuneesta muutoksesta.
- Handlerin suoritus käynnistetään notify-avainsanalla.
- Yksi tehtävä voi ilmoittaa muutoksesta useammalle handlerille.
- Handlerit suoritetaan siinä järjestyksessä, jossa ne on määritelty handlers-osiossa, eikä notify-listan järjestyksessä.
- Jos useampi tehtävä kutsuu samaa handleria, se suoritetaan silti vain kerran kyseisessä suorituskierroksessa.
Oma havainto: Handlerit tukevat Ansiblen idempotenttia toimintaa, sillä palveluita ei tarvitse käynnistää uudelleen, jos konfiguraatio ei ole muuttunut. Mitä tapahtuu, jos tehtävä ilmoittaa handlerille muutoksesta, mutta playbookin myöhempi tehtävä epäonnistuu ennen handlerin suorittamista?

### ansible-doc service
- Service-moduuli tukee useita palvelunhallintajärjestelmiä, kuten systemd, SysV ja OpenRC.
- service tunnistaa automaattisesti, mitä palvelunhallintajärjestelmää kohdekone käyttää, ja käyttää sille sopivaa moduulia.
- Kaikki palvelunhallintajärjestelmät eivät tue samoja toimintoja.
- Windows-koneiden palveluiden hallintaan käytetään erillistä ansible.windows.win_service-moduulia.

Optiot:

| Optio | Selitys |
|---|---|
| `enabled` | Määrittää, käynnistyykö palvelu automaattisesti koneen käynnistyessä (true/false). |
| `name` | Hallittavan palvelun nimi. |
| `state` | Palvelun haluttu tila (started, stopped, restarted, reloaded). |

Esimerkki:
```	
- name: Start Apache and enable on boot
  ansible.builtin.service:
    name: apache2

    state: started
    enabled: true
```
- Käynnistää Apache2-palvelun, jos se ei ole jo käynnissä, ja määrittää palvelun käynnistymään automaattisesti koneen käynnistyessä.

## a) Apassi. Asenna Apache 2 käsin. Weppisivun tulee näkyä palvelimen etusivulla. Sivun tulee olla tavallisen käyttäjän muokattavissa, ilman root- tai sudo-oikeuksia.


## b) Moottorix. Asenna Nginx käsin. Weppisivun tulee näkyä palvelimen etusivulla. Sivun tulee olla tavallisen käyttäjän muokattavissa, ilman root- tai sudo-oikeuksia. (Muista sammuttaa Apache ensin.)


## c) Automoottorix. Automatisoi Nginx asennus Ansiblella. Ylläpitäjän osuus Ansiblella riittää, itse HTML-weppisivut voi tehdä käsin.


## Lähteet
Karvinen, T 1. 2026. Palvelinten Hallinta. Luettavissa: https://terokarvinen.com/palvelinten-hallinta/. Luettu: 6.11.2026


