# h12 - vianSelvitys Sunnuntai 5.3.2023

## Luodaan ja analysoidaan ongelmia Djangon tuotantotyyppisessä asennuksessa

### ALKUTILANNE

![Screenshot 2023-03-05 at 21 45 00](https://user-images.githubusercontent.com/104775534/222982177-3cca42ce-092f-4919-ba6a-cc81e73dbbab.png)


### a - luodaan kirjoitusvirhe Python tiedostossa

Kirjoitetaan manage.py pikku virhe STATIC_URL:iin

![Screenshot 2023-03-05 at 21 53 21](https://user-images.githubusercontent.com/104775534/222982576-d77620bf-79e5-4905-8738-87b1059aaae3.png)

Päivitetään manage.py

    touch wsgi.py
    
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

### c - projektikansiolla väärät oikeudet

Tätä en osaa niin en uskaltanut rupee säätää.

### d - kirjoitusvihe Apachen conf tiedostoon

    cd /etc/apache2/sites-available/
    sudoedit jeremyco.conf
    /sbin/apache2ctl configtest # Aina kannattaa ennen restarttia tehdä.
    sudo systemctl restart apache2 
    

Kommentoidaan tuo VirtualHost kohta 

![Screenshot 2023-03-05 at 22 25 03](https://user-images.githubusercontent.com/104775534/222983995-e27a3193-0421-4946-aa68-d83633f7b38f.png)

    /sbin/apache2ctl configtest
    
![Screenshot 2023-03-05 at 22 27 58](https://user-images.githubusercontent.com/104775534/222984149-ad0fb711-d168-4a51-bdd5-d1bfae6b23cf.png)

![Screenshot 2023-03-05 at 22 31 04](https://user-images.githubusercontent.com/104775534/222984318-98eac45a-5f28-418a-852f-202c18251baf.png)

![Screenshot 2023-03-05 at 22 31 32](https://user-images.githubusercontent.com/104775534/222984346-9895bac4-77a2-4ba5-9aec-4ca67886cc79.png)

    
