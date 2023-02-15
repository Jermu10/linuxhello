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

![Screenshot 2023-02-16 at 1 08 39](https://user-images.githubusercontent.com/104775534/219211042-d805fb61-93ed-4460-a212-4fcd82e1b2db.png)

Kun käyttäjän perässä näkyy => on sovellus käynnissä ja voi kirjoittaa SQL:ää.

## b - Kokeile CRUD (create, read, update, delete) läpi

### Aloitetaan luomalla taulu ja sinne muutama tieto

Luodaan taulu ja määritetään, että jokaisen taulun tiedolla on id numero, joka on sen pääavain sekä nimi jossa saa olla max 200 merkkiä.

    CREATE TABLE fruits (id SERIAL PRIMARY KEY, name VARCHAR(200));

Lisätään tauluun banaani ja katsotaan menikö se tauluun

    INSERT INTO fruits(name) VALUES ('Banana');
    SELECT * FROM fuits;
    
![Screenshot 2023-02-16 at 1 19 30](https://user-images.githubusercontent.com/104775534/219214366-cc66f975-cb06-43e7-8178-ab072d981c31.png)

### Muokataan 'Banana' ja poistetaan 'Mango'

    UPDATE fruits SET name='Banaani' WHERE name='BANANA';

    DELETE FROM fruits WHERE name='Mango';

    SELECT * FROM fruits

![Screenshot 2023-02-16 at 1 26 49](https://user-images.githubusercontent.com/104775534/219215604-5b947b08-b154-497d-b4fd-ee09100b9b79.png)



## Kättelyt 01.28

Kaikki sujui mallikkaasti niinkuin tunnillakin ja opin luomaan tietokannan koneelleni. Aikaa kului 45min.

## Lähteet

https://terokarvinen.com/2016/03/03/install-postgresql-on-ubuntu-new-user-and-database-in-3-commands/?fromSearch=postgre, https://terokarvinen.com/2016/postgresql-install-and-one-table-database-sql-crud-tutorial-for-ubuntu/, https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/




