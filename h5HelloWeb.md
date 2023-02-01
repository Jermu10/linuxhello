# 1.2.2023 15:07

## Tehtävä x - kuuntele podcast

Kuuntelin Indie Hackersin uusimman (#266) jakson, jossa Mat De Sousa kertoi urastaan Shopify sovellus kehittäjänä. 

https://share.transistor.fm/s/940ae75e

Shopify sovellus on kauppasivusto, missä Shopify myyjä voi myydä tuotteitaan.
Shopifylla on omakin sovellus, mutta siinä ei ole kaikkea, mitä myyjät haluavat. Joten markkinarako oli olemassa.

- Aloitti luomaan shopify sovelluksia, mutta kukaan ei aluksi ollut kiinnostunut
- Muutaman yrityksen jälkeen, hän lähti kyselemään Facebook sivustoilta (shopify kauppioiden), että minkälaista kaikkea he oikein tarvitsisivat sovellukseltaan
- Tämän jälkeen hän teki sovelluksen, joka sai suosiota vähän.
- Isoin muutos tapahtui (suosion kasvu), kun hän rupesi seuraamaan asiakkaidensa dataa ja muokkaamaan sovellusta sen mukaan
  - Hänen Conversation rate (sivuston vierailijat jaettuna ostot) yli tuplaantui
  - Esim. näyttämällä visuaalisest alussa, mitä kaikkea mitäkin nappula tekee


## Tehtävä a - Vaihda apache esimerkkisivu joksikin muuksi 

Alkutilanne

![Screenshot 2023-02-01 at 17 45 43](https://user-images.githubusercontent.com/104775534/216091733-89aaf8aa-8f8a-4440-afa8-3af2bcbf74e8.png)

Muokkasin tiedostoa microlla: Poistin kaikki html jutut ja jätin tilalle vain tekstin. Kun tallensin micro pyysi, että tallennetaanko tämä sudona (vaati siis, että pitää olla sudo jos haluaa tallentaa,
jonka jälkeen laitoin salasanani ja done.

![Screenshot 2023-02-01 at 17 50 26](https://user-images.githubusercontent.com/104775534/216093388-2dd10d4f-bced-46c4-8447-44a800795e16.png)

Ja tässä kun menee localhostiin niin pelkkä microon laittamani teksti näkyy.

![Screenshot 2023-02-01 at 17 52 30](https://user-images.githubusercontent.com/104775534/216093931-a48dabb1-472b-4562-b99f-a075dfa843e5.png)


## TehtäväT b JA c - Tee uusi käyttäjä ja sille toimiva nettisivu localhos/~testi

Ymmärtääkseni tässä tehdään sama asia ja tein jo omalle käyttäjälleni oman sivun niin teen uudestaan step by step, mutta tehtävä C mukaan eli uusi käyttäjä. En siis uskalla poistaa kaikkea tekemiäni juttuja b tehtävään. :)

Tässä b tulos

![Screenshot 2023-02-01 at 18 03 13](https://user-images.githubusercontent.com/104775534/216096632-8485be0a-f105-4a75-b4f5-f0f2236ca467.png)


### Tehdään uusi käyttäjä:
  
    sudo adduser testi
  
    sudo usermod -aG sudo testi

Sitten mennään testaamaan sillä käyttäjällä tuliko sudo oikeudet. Ja tulihan ne (jos sudo whoami output on root).

![Screenshot 2023-02-01 at 18 16 43](https://user-images.githubusercontent.com/104775534/216099866-b6e2a3ed-251c-4eac-bab5-1fc00dc4b7ab.png)

### Tehdään uudelle "testi"-käyttäjälle omat nettisivut localhost/~testi

Alkutilanne

![Screenshot 2023-02-01 at 18 20 40](https://user-images.githubusercontent.com/104775534/216100895-aca97957-0bef-4317-bef3-7e50b980ac28.png)

Olettamukseni on että vaiheet:

    sudo a2enmod userdir
    sudo /etc/init.d/apache2 restart

Ei tarvitse tehdä uudella käyttäjällä, koska se on jo kerran tehty aikaisemmin toisella käyttäjällä, mutta samalla juuri käyttäjällä.

Seuraavaksi tehdään public_html kansio käyttäjän hakemistoon:

    mkdir public_html
  
Tämän jälkeen nettisivulla localhost/~testi näkyy hakemisto:

![Screenshot 2023-02-01 at 18 29 24](https://user-images.githubusercontent.com/104775534/216103413-f7b39b68-4c1f-45ac-9d3e-f2448f9510cf.png)

Sitten tehdään vielä nettisivu:

    cd public_html
  
    micro index.html
  
Tämän jälkeen näkyy: 
  
![Screenshot 2023-02-01 at 18 31 26](https://user-images.githubusercontent.com/104775534/216103855-23e208a5-d0e4-4754-ae73-38ebd8c43cc6.png)


## Tehtävä c - Tee validi HTML5 sivu
  
  Teen nyt oman käyttäjäni sivun (localhost/~jeremy) html muotoiseksi: 
  
  Elikkäs mennää sinne public html kansioon ja muokataan index.html kansiota ja kirjotellaa sinne maailman yksinkertaisinta html:ää.
  
  
  ![Screenshot 2023-02-01 at 18 44 44](https://user-images.githubusercontent.com/104775534/216107004-7078e3d7-381f-451e-a347-c06861f93674.png)

Ja lopputulos: 

![Screenshot 2023-02-01 at 18 45 19](https://user-images.githubusercontent.com/104775534/216107140-b60cf039-0735-4c51-9273-a150c8a11cbd.png)

  
## Kättelyt 

Tehtävään kului aikaa n. tunti plus podcast puol tuntii. Opin ymmärtämään enemmän miten linuxissa hommat toimii ja hemmetin hyvän podcastin.
Toivottavasti ymräsin tehtävä b oikein ja, että vastaukseni on riittävä.

## Lähteet: 

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/
https://terokarvinen.com/2008/install-apache-web-server-on-ubuntu-4/
https://linuxize.com/post/how-to-create-a-sudo-user-on-debian/
https://share.transistor.fm/s/940ae75e
