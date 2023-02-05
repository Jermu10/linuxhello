# H6 Sunnuntai 5.2.2023

## x - lue ja tiivistä 

### Apache Software Foundation 2023: Getting Strated https://httpd.apache.org/docs/2.4/getting-started.html

- Internetin osoitteet esitetään URL:na - Uniform Resource Locators
- Samalla ip-osoitteella voi olla monia hostnameja
- Yhdistääkseen serveriin, asiakkaan pitää laittaa serverinnimi ip-osoitteeksi(?)
- Nettisivuilla voi olla staattista ja dynaamista "materiaalia"

### Apache SoftWare Foundation 2023: Name-based Virtual Host Support https://httpd.apache.org/docs/current/vhosts/name-based.html

- IP-pohjainen virtuaali hostaus käyttää ip osoitetta yhdistääkeen oikeaan palvelimeen ja vaatii erillisen IP-osoitteen jokaiselle palvelimelle
- Nimipohjainen virtuaalipalvelin ottaa asiakkaan ilmoittaman hostnamen HTTP palkkiin.
-  Kun pyyntö tulee serveri etsii <VirtualHost> parhaan osuman IP-osoitteen ja pyytäjän portin perusteella.


## a - Vaihda Apachen esimerkkisivu omaan!

Alkutilanne
    
[Screenshot 2023-02-05 at 22 48 09](https://user-images.githubusercontent.com/104775534/216844987-b46148db-c895-44b5-b49e-8ed9ca37d300.png)


Luodaan koti hakemistoon directory ja sinne haluama html sivu

    mkdir public_sites
    cd public_sites
    micro index.html
    
 Seuraavaksi mennään apachen sites-available directoryyn ja luodaan sinne etusivu.conf tiedosto
 
    cd /etc/apache2/sites-available
    sudoedit etusivu.conf
    
 Sitten kirjoitetaan etusivu.conf tiedostoon rootti, mistä nettisivu haetaan
 
    <VirtualHost *:80>
      DocumenRoot /home/jeremy/public_sites/
      <Directory /home/jeremy/public_sites/>
      require all granted
      </Directory>
    </VirtualHost>
    
  Seuraavaksi siirretään etusivu.conf aktiiviseksi kotisivuksi ja otetaan aikaisempi sivu veks. Ja päivitetään muutokset
    
        sudo a2ensite etusivu.conf
        sudo a2dussute 000-default.conf
        sudo systemctl restart apache2
        
Ja loppunäkymä kun sivu päivitetään:

![Screenshot 2023-02-05 at 23 02 24](https://user-images.githubusercontent.com/104775534/216845602-0246bdfd-4eba-4476-b522-5b90e1275c40.png)

Kokeillaan tehdä myös muokkaus sivulle ilman sudoa:
  
    micro public_sites/index.html
    
![Screenshot 2023-02-05 at 23 06 28](https://user-images.githubusercontent.com/104775534/216845798-375b11d9-4e4a-4792-bbf7-b69e12750add.png)


## Tehtävä b tee asetustiedostoon virhe ja etsi se

Alkutilanne: Otin 'reguire all granted' pois etusivu.conf-tiedostosta ja restarttasin apachen. Kotisivun näkymä muuttui täksi: 
  
![Screenshot 2023-02-05 at 23 17 54](https://user-images.githubusercontent.com/104775534/216846374-2a91a93b-2bd2-41ee-be7c-07d2822825db.png)

menin katsomaan apachen error.logit ja sinne oli ilmestunyt tälläista:
        
![Screenshot 2023-02-05 at 23 22 10](https://user-images.githubusercontent.com/104775534/216846773-e661eebc-e4cc-4874-8423-cc2f976f47b6.png)

Elikkä authz_core:error tuli, joka voisikin jo viitata, että nyt ei ole asetuksissa kaikkia oikeuksia annettu. Pid:hän oli tuo prosessin id.

Sitten kävin katsomassa apache2ctl configtestin:

![Screenshot 2023-02-06 at 0 01 05](https://user-images.githubusercontent.com/104775534/216848416-cde4f30b-69c7-465f-b541-4979a3769f5e.png)

Ei sano vielä mitään, mutta katotaan miten muuttuu kun korjataan tilanne. UPDATE: Korjatussa ei ollut mitään erilailla tuohon eli ei virheitä.

### Tiedostojen vertaus

Sain tiedostot näkymään kivasti päällekkäin ilman defaultin kommentteja tällä komennolla:

![Screenshot 2023-02-06 at 0 22 22](https://user-images.githubusercontent.com/104775534/216849282-8bcde615-ac3a-4ca4-a01f-832631969739.png)


Korjasin virheen ja kokeilin että sivu taas toimii:

![Screenshot 2023-02-06 at 0 31 56](https://user-images.githubusercontent.com/104775534/216849680-57771a09-b952-47dc-9d3f-24885fbf91e8.png)


## Kättelyt

Aikaa meni n. 2h. Tein ekan tehtävän vikana ja luetunymmärtäminen oli tähän aikaan illasta kyllä tuskaisaa. Hyvin rupeaa jo tuolla komentokentässä löytymään okea directoryt jne.

Lähteet: https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/
https://jvaris.wordpress.com/2014/03/03/linux-server-task-5-apache-name-based-virtual-hosting/
https://httpd.apache.org/docs/2.4/getting-started.html
https://httpd.apache.org/docs/current/vhosts/name-based.html

