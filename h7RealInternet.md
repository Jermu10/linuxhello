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
        
   
   
   
   
   
   
   
