# Sunnuntai 29.1.2023 19:30

## Tehtävä x lue ja tiivistä

Otin PUTORIUS nettisivulta tekstin, jossa internet yhteyden kokeilua voidaan suorittaa suoraan Linuxin komentoriviltä.
https://news.ycombinator.com/item?id=21572308
https://www.putorius.net/speed-test-command-line.html

- Speedtest.net nettisivun sijaan voisi yhteyttä suoraan testata Linux komentorivillä
- Tässä muutama vaihtoehto:
  -Unofficial Speedtest-CLI Python Script
    -Helppo asentaa
  -Official Ookla Speedtest CLI
    -Ooklan tekemä (sama kuin speedtest.net)
    -Helppo käyttöinen ja ymmärtää
    -Käyttö rajattu lähimmille servereille
  -Debain repositoryn speedtest-cli
    -Käyttää speedtest.net palvelua
  -iper
    -Antaa luoda oman testaus infran:
      -"Run it as a server on one end you want to test, then run it as client against that server IP/hostname on the other end."
      
## Tehtävä a Tukki. Analysoi yksi esimerkkirivi kustakin lokista
### /var/log/syslog - yleisloki
Sain nämä kaikki lokit kun avasin firefoxin. Päiväys on oikein, mutta kello ei. Avasin selaimen klo: 21:50 suomen aikaa.
rkit-daemon on ilmeisesti prosessorin säätelijä, joka säätelee prosessorin tehtäviä ja varmistaa, että ne tulee tehtyä ajallaan.
Tässä se valvoo Yhden käyttäjän kahden prosessin neljää "ketjua"
    
    ![Screenshot 2023-01-29 at 21 51 24](https://user-images.githubusercontent.com/104775534/215352260-4574f527-a494-48eb-b8f4-6e43a11409a9.png)

### /var/log/auth.log - Näyttää kirjautumiset ja sudon käytön

Tässä lokissa näkyy kuinka aikaisemman tehtävässä, jotta sain syslogin luettua, minun piti käyttää sudoa.

![Screenshot 2023-01-29 at 22 02 55](https://user-images.githubusercontent.com/104775534/215352744-ebac53a7-9b1b-4162-8d6d-5ea42cb84f34.png)

### /var/log/apache2/acces.log - 

![Screenshot 2023-01-29 at 22 14 16](https://user-images.githubusercontent.com/104775534/215353402-37d277a8-0bfe-4c77-a035-02e5d72a8fe2.png)


![Screenshot 2023-01-29 at 22 16 50](https://user-images.githubusercontent.com/104775534/215353523-3ef665d1-9fdd-45bb-b411-de0426225125.png)

