# h9 - Sequal Torstai 16.2.2023 00:45 

    Specs:
    Apple M1 Pro
    Cores 10
    Memory 16GB
    macOS Ventura 13.2

## x - Esimerkki palvelusta, jota käytetään wepissä selaimella, koodi ajetaan palvelimella ja taustalla on tietokanta

Käytetään esimerkkinä jotain verkkokauppaa esim. Gigantti. Webbiselaimella voi selata tuotteita, jotka palvelin hakee tietokannasta. 
--> Asiakas haluaa tuotteen --> palvelin hakee tietokannasta, onko tuotteita jäljellä ja missä --> asiakas tilaa tuotteen --> palvelin tekee tilaus pyynnön joka näkyy myyjälle.

-   Nettisivulla pelkkä käyttöliittymä, joka näyttää tuotteet, jotka ollaan haettu palvelimen avulla tietokannasta
-   Webbiselaimen käyttö: 
    - Tekee käyttöliittymästä "kevyitä" ja nopeasti suoriutuvia
    - Toimii useammilla laitteilla
- Backendi palvelimella helpottaa monella tavalla
    - Käyttäjän ei tarvitse ladata ja päivitellä mitään ohjelmaa omalla koneella
    - Backendin päivitys ja muokkaus helppoa, koska vain yhdessä paikkaa mistä moni pääsii käsiksi


## a - Asennetaan Postgre

### Ladataan PostgreSQL, luodaan käyttäjä ja käynnistetään sovellus

    sudo apt-get update
    sudo apt-get -y install postgresql

    sudo -u postgres createdb testi
    sudo -u postgres create user testi

    psql

