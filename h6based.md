# H6 Sunnuntai 5.2.2023

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

Alkutilanne: Otin 'reguire all granted' pois ja restarttasin apachen. Kotisivun näkymä muuttui täksi: 
  
![Screenshot 2023-02-05 at 23 17 54](https://user-images.githubusercontent.com/104775534/216846374-2a91a93b-2bd2-41ee-be7c-07d2822825db.png)

menin katsomaan apachen error logit ja sinne oli ilmestunyt tälläista:
        
![Screenshot 2023-02-05 at 23 22 10](https://user-images.githubusercontent.com/104775534/216846773-e661eebc-e4cc-4874-8423-cc2f976f47b6.png)

Elikkä authz_core:error tuli, joka voisikin jo viitata, että nyt ei ole asetuksissa kaikkia oikeuksia annettu. Pid:hän oli tuo prosessin id.


        
    
