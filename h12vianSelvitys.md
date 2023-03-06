# h12 - vianSelvitys Sunnuntai 5.3.2023

## Luodaan ja analysoidaan ongelmia Djangon tuotantotyyppisessä asennuksessa

### ALKUTILANNE

![Screenshot 2023-03-05 at 21 45 00](https://user-images.githubusercontent.com/104775534/222982177-3cca42ce-092f-4919-ba6a-cc81e73dbbab.png)


### a - luodaan kirjoitusvirhe Python tiedostossa

Kirjoitetaan manage.py pikku virhe STATIC_URL:iin

![Screenshot 2023-03-05 at 21 53 21](https://user-images.githubusercontent.com/104775534/222982576-d77620bf-79e5-4905-8738-87b1059aaae3.png)

Päivitetään manage.py

    touch wsgi.py # Tämä riitti päivittääkseen sivun
    sudo systemctl restart apache2
    
TULOS: 

![Screenshot 2023-03-05 at 21 55 37](https://user-images.githubusercontent.com/104775534/222982669-c8490d12-68c9-4616-9427-d92dc935110d.png)

Ei tullut lokeihin mitään erroreita. Vain tyylit lähti.

### b - Djangon projektikansio eri paikassa (missä manage.py)

Siirretään kansio 

    cd publicwsgi
    mv jeremyco ..
    
TULOS: 

![Screenshot 2023-03-05 at 22 05 26](https://user-images.githubusercontent.com/104775534/222983159-af7494c1-08bb-44f0-ac4f-75689c08209e.png)

![Screenshot 2023-03-05 at 22 12 28](https://user-images.githubusercontent.com/104775534/222983450-5defb94b-5cdb-4d78-ae8c-47aea5e5ed1e.png)

- authz_core:error = oikeuksiin liittyvä error
- pid = process id
- client = käyttäjä
- AH01630: client denied by server configuration = Palvelin estää asiakasta määritysten takia(conf)

Eli yritti päästä noihin kansioihin, mitkä on conffissa asetettu, mutta ei pääse niihin koska ne on siirretty.

### c - projektikansiolla väärät oikeudet

Otetaan projektilta oikeudet veks

    chmod ugo-rwx jeremyco
    
![Screenshot 2023-03-05 at 23 18 55](https://user-images.githubusercontent.com/104775534/222986614-43ba7808-fd68-4941-a8cc-28c19fde43b1.png)

![Screenshot 2023-03-05 at 23 19 41](https://user-images.githubusercontent.com/104775534/222986643-e52adb56-b953-4803-a695-6d36087000bd.png)

- core:error = perus virhetila
- pid = process id
- (13)Permission dedied = 13 lupaa kiellettiin
- AH00035: access to .. because search permission are missing on a component of path = 
    - Projektilla ei ole luku oikeuksia niin ei pääse lukemaan /admin/login/
    - Toisessa ei pääse lukemaan /faviacon.ico
    - referer: http://localhost/admin/login/?next?/admin/ = viittaa tähän sivustoon

Palautetaan oikeudet `chmod 755 jeremyco`


### d - kirjoitusvihe Apachen conf tiedostoon

    cd /etc/apache2/sites-available/
    sudoedit jeremyco.conf
    /sbin/apache2ctl configtest # Aina kannattaa ennen restarttia tehdä.
    sudo systemctl restart apache2 
    

Kommentoidaan tuo VirtualHost kohta 

![Screenshot 2023-03-05 at 22 25 03](https://user-images.githubusercontent.com/104775534/222983995-e27a3193-0421-4946-aa68-d83633f7b38f.png)

    /sbin/apache2ctl configtest
    
![Screenshot 2023-03-05 at 22 27 58](https://user-images.githubusercontent.com/104775534/222984149-ad0fb711-d168-4a51-bdd5-d1bfae6b23cf.png)

- Kertoo aika tarkasti, että Syntax error löytyy tiedostosta /etc/apache/sites-enabled/jeremyco ja rivillä 24
    - Löytyy </VirtualHost> muttei <VirtualHost>
- configtest failed = testi epäonnistui
- Kertoo vielä, ett' errpr logissa voi olla enemän tietoa. Tuskin tuon tarkemmin voi kertoakkaan, mutta mennään katsomaan
  

![Screenshot 2023-03-05 at 22 31 04](https://user-images.githubusercontent.com/104775534/222984318-98eac45a-5f28-418a-852f-202c18251baf.png)

`sudo systemctl restart apache2` komentoa yrittäessä tuli, ettei apache2.service ei onnistunut, koska hallinta prosessista tuli error
    
![Screenshot 2023-03-05 at 22 31 32](https://user-images.githubusercontent.com/104775534/222984346-9895bac4-77a2-4ba5-9aec-4ca67886cc79.png)

Tämä ei niinkään error, mutta kertoo, että SIGTERM (ilmeisesti restart prosessi) jäi kesken ja serveri sammutetaan
    
### e - Apache wsgi-moduuli puuttuu 

    sudo apt-get purge libapache2-mod-wsgi-py3
    
![Screenshot 2023-03-05 at 22 46 36](https://user-images.githubusercontent.com/104775534/222984985-91eef49f-1b78-447a-8ae2-cf787fbbf769.png)

kokeilin `touch wsgi.py` jos localhostiin saisi errorin, mutta ei saanut. Jälkeen päin mietittynä olisi ehkä pitänyt kokeilla restarttaa apache2 `sudo systemctl restart apache2`

Tämä oli ainut error minkä löysin. Tämä configtestistä.
    
- Syntax error conf tiedostossa jälleen.
- invalid command 'WSGIDaemonProcess' = virheellinen komento
    - kertoo, että voisi johtua kirjotusvirheestä tai, että moduulia ei oli palvelimen määrityksissä
    - error.logeissa ei mitään

![Screenshot 2023-03-05 at 22 49 53](https://user-images.githubusercontent.com/104775534/222985182-de3ba764-f49c-47e9-ab81-e3c0d472dc38.png)
    


### f - Väärät domain-nimet ALLOWED_HOSTS kohtaan (manage.py ja DEBUG pitää olla False)

![Screenshot 2023-03-05 at 23 05 27](https://user-images.githubusercontent.com/104775534/222985947-f54b831b-1709-4153-af19-cda50f952d07.png)

    sudo systemctl restart apache2 
    
TULOS: 

![Screenshot 2023-03-05 at 23 05 50](https://user-images.githubusercontent.com/104775534/222985973-9b9ab4dd-894a-4aa7-b1d0-23034cadce04.png)

Lokeissa ei näy mitään virheitä. Oletan, että ainut error pitääkin näkyä localhostissa, koska sen oikeudet näyttää mitään vietiin pois.


## Kättelyt
    
Aikaa meni n. 2tuntia. Vähän työlästä ja väsynyttä mikä näkyy tehtävissä.
    
### Lähteet
    
- https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/
- https://stackify.com/apache-error-log-explained/

