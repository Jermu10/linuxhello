# Tiistai 7.2.2023 22:30

    Specs:
    Apple M1 Pro
    Cores 10
    Memory 16GB
    
    
Haluan alkuun suositella kaikkia tallentemaan aina välillä md tiedostoa, jos vaikka sattuu käymään niin, että juuri kun olet tehnyt koko jutun valmiiksi painat väärää nappia ja kaikki katoaa :) 

## Tehtävä x - Lue ja tiivistä https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/

- Luo palvelin jossain palvelussa esim. Linode
- Muista hyvät salasanat
- Laita palomuuri päälle ja musita tehdä reiät 22/tcp ja 80/tcp
- Tee uusi käyttäjä ja poista mahdollisuus kirjautua roottiin
- Päivitä sovellukset
  
## Tehtava a - Vuokraa oma virtuaalipalvelin

Päätin vuokrata virtuaalipalvelimen DigitalOceanilta.
Rekistöröityminen meni kivuttomasti.

## Tehtava b - Tee alkutoimet virtuaalipalvelimellasi.

Ota palvelimeen yhteys ja asenna ufw, salli ssh yhdistelmä ja käynnistä.

    ssh root@IP-osoite
    
    sudo apt-get update
    sudo apt install ufw
    sudo ufw allow 22/tcp
    sudo ufw enable
    
  Tehdään uusi käyttäjä ja kokeillaan saako sillä yhteyden:
  
    sudo adduser severi
    sudo adduser severi sudo
    
    ssh severi@IP-osoite
    
  Lukitaan root:
  
    sudo usermod --lock root
    sudoedit /etc/ssh/sshd_config // Muokataan PermitRootLogin 'yes --> 'no'
    sudo service ssh restart
    
  Sitten päivitellään järjestelmä ja siinä välissä tuli apache2 ladattua:
  
        sudo apt-get update
        sudo apt install apache2
        sudo apt-get upgrade // toivottavasti tämäkin piti tehdä
        
   Apache latauksen jälkeen, ei tarvinut tehdä viimetunnilta tuttua 'systemctl apache2 start' tai joku sinnepäin. Nettisivu toimi silti.
   
   
 ## Tehtävä c - Muokkaa weppipalvelimen testisivua ja salli palomuurista 80/tcp
 
Alkutilanteen kuva katosi, mutta kun yritti mennä ip-osoitteen nettisivulle, mitään ei tapahtunut ja näytti, että lataa vain.

Sitten muokataan testisivua ja tehdään reikä palomuuriin:

    echo testi | sudo tee /var/www/html/index.html
    sudo ufw allow 80/tcp
   
   Ja tulos: 
   
   ![Screenshot 2023-02-08 at 0 03 07](https://user-images.githubusercontent.com/104775534/217376870-1d650a71-a7cb-4ec1-9ba6-f51c50b2bc15.png)

   
## Tehtävä d - etsi murtautujia

Etsin murtautujia:

    sudo less /var/log/auth.log
    
-   Ilmeisesti tässä on sshd[29113] on tapahtuman id. ja authentication failure johtuu vääristä tunnuksista mitkä käyttäjä antanut(?)
-   Sitten seuraavassa logissa sanotaan, että failed password for root from ilmeisesti kirjautujan IP-osoitteesta
    
![Screenshot 2023-02-08 at 18 20 53](https://user-images.githubusercontent.com/104775534/217588907-928eed07-8780-4198-aa3e-9eebfa0aaf51.png)

Tässä näkyy kuin menin puhelimellani nettisivulle. Kertoo aika tarkasti puhelimen käyttöjärjestelmän-, liittymän- ja Safarin versiot

 ![Screenshot 2023-02-08 at 18 41 23](https://user-images.githubusercontent.com/104775534/217594542-c48e9203-91ab-41ed-9ecd-4a8de4e8bb70.png)


