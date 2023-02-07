# Tiistai 7.2.2023 22:30

    Specs:
    Apple M1 Pro
    Cores 10
    Memory 16GB
    
    
Haluan alkuun suositella kaikkia tallentemaan aina välillä md tiedostoa, jos vaikka sattuu käymään niin, että juuri kun olet tehnyt koko jutun valmiiksi painat väärää nappia ja kaikki katoaa :) 
  
## Tehtava a - Vuokraa oma virtuaalipalvelin

Päätin vuokrata virtuaalipalvelimen DigitalOceanilta.
Kirjoitin aikasemmin kaikki kivasti, että mitä kannattaa ottaa huomioon mutta nyt en jaksa koska vituttaa

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
