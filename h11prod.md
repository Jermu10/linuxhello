# h11 - prod Keskiviikko 1.3.2023 klo 20.20

    Specs:

    Apple M1 Pro
    Cores 10
    Memory 16GB
    macOS Ventura 13.2


## a - Tee Djangon tuotantoasennus

### Alkutilanne localhost: 

![Screenshot 2023-03-01 at 20 25 42](https://user-images.githubusercontent.com/104775534/222229739-589d8840-fc26-42b2-b7ba-17c2d5d49a74.png)

### Seuraavaksi luodaan uudelle django sivustolle kansiot ja staattinen sivu

    mkdir -p publicwsgi/jeremyco/static/
    cd publicwsgi/jeremyco/static/
    micro index.html
    
### Seuraavaksi käydään luomassa conf tiedosto apache2/sites-available 

    cd /etc/apache2/sites-available/
    sudoedit jeremyco.conf
    
Kävin kopoimassa vanhasta conf tiedostosta mallin ja muutan siinä DocumentRootin oikeaksi Aliakseksi ja Directoryn oikeaksi:

![Screenshot 2023-03-01 at 20 42 20](https://user-images.githubusercontent.com/104775534/222234877-4b1e1967-a445-4886-8832-6de2696ce94b.png)

### Seuraavaksi otetaan uusi conf tiedosto käyttöön ja vanha pois käytöstä. Tehdään myös configtest.

    sudo a2ensite jeremyco.conf
    sudo a2dissite etusivu.conf
    /sbin/apache2ctl configtest
    
![Screenshot 2023-03-01 at 20 49 06](https://user-images.githubusercontent.com/104775534/222236122-cae05d99-783b-4272-83bf-e358b55bab91.png)

Testi ok, joten käynnistetään apache2 uusiksi

    sudo systemctl restart apache2
    
Ei menny niiku strömsöössä. käydään tutkimassa conf tiedostoa uusiksi..

![Screenshot 2023-03-01 at 20 56 44](https://user-images.githubusercontent.com/104775534/222237669-c6d1d189-7d8a-4aeb-8e8d-f1cf50a71059.png)

Conf tiedostossa oli /static/ kirjoitettu isolla, siksi ei löytynyt. Uusi apache2 restart ja tulos: 

![Screenshot 2023-03-01 at 20 59 08](https://user-images.githubusercontent.com/104775534/222238118-d10f0968-186a-4279-a0df-3c9a5de3fb6d.png)


### Seuraavaksi luodaan virtuaaliympäristö (virtualenv) luomaamme "django" kansioihin.

    cd publicwsgi/
    virtualenv -p python3 --system-site-packages env
    
### Asennetaan Django ympäristöön

    source env/bin/activate
    micro requirements.txt # kirjoitetaan tiedostoon vain django
    pip install -r requirements.txt
    
Tulos: 

![Screenshot 2023-03-01 at 21 09 52](https://user-images.githubusercontent.com/104775534/222240300-8599bbdd-e59c-4ca4-b766-f9fd3f89e424.png)

    
### Luodaan uusi django projekti

    django-admin startproject jeremyco


![Screenshot 2023-03-01 at 21 12 09](https://user-images.githubusercontent.com/104775534/222240765-5d1cfa4b-671d-4e25-ae9b-d38ab43835cf.png)

Ei onnannu. Nyt ihan omasta päästäni kokeilen:

    cd jeremyco
    django-admin startproject


![Screenshot 2023-03-01 at 21 13 18](https://user-images.githubusercontent.com/104775534/222240998-0e011ae1-3d34-4e0e-aff3-c04626ddcb81.png)

No ei se nyt ihan lähteny.. Poistetaan jeremyco ja sen sisältö ja sitten luodaan.

    rm -r jeremyco
    django-admin startproject jeremyco

### Seuraavaksi yhdistetään apache ja django muokkaamaalla jeremyco.cong tiedostoa

    sudoedit /etc/apache2/sites-available/jeremyco.conf


![Screenshot 2023-03-01 at 21 26 41](https://user-images.githubusercontent.com/104775534/222243871-6d704b57-ebc4-4919-94c1-08ee94df4b05.png)


### Seuraavaksi asennetaan Apache WSGI moduuli, jotta apache ymmärtää mitä WSGI komennot tarkoittavat. 
    
    sudo apt-get update
    sudo apt-get -y install libapache2-mod-wsgi-py3

Tehdään taas configtest

    /sbin/apache2ctl configtest
    
![Screenshot 2023-03-01 at 21 32 26](https://user-images.githubusercontent.com/104775534/222245011-bb58ea1c-742b-4ad1-9dd4-35e685616c1e.png)

Käynnistetään apache uusiksi ja tarkistetaan onnistuiko

    sudo systemctl restart apache2
    curl -s localhost|grep title
    curl -sI localhost|grep Server

![Screenshot 2023-03-01 at 21 42 51](https://user-images.githubusercontent.com/104775534/222247350-1d8f4ade-7af7-46dd-b030-75be8e4a308b.png)


![Screenshot 2023-03-01 at 21 43 07](https://user-images.githubusercontent.com/104775534/222247416-76f43737-e5d5-43f3-83fc-b62feba47581.png)


![Screenshot 2023-03-01 at 21 40 01](https://user-images.githubusercontent.com/104775534/222246584-57adfd15-55db-4aa5-85d7-c6d50c4acffa.png)

Kaikki näyttää siltä miltä pitääkin!

### Otetaan DEBUG pois päältä

    cd
    cd publicwsgi/jeremco/jeremyco
    micro settings.py
    
Muokataan DEBUG = False ja lisätään ALLOWED_HOSTS

![Screenshot 2023-03-01 at 21 51 37](https://user-images.githubusercontent.com/104775534/222250768-13649bab-921a-49db-94ae-41f74a19af40.png)

Päivitetään ilman sudoa

    touch wsgi.py
    
Tulos: 

![Screenshot 2023-03-01 at 21 54 26](https://user-images.githubusercontent.com/104775534/222251303-941205fd-0f56-4048-8802-95da30bfde17.png)

![Screenshot 2023-03-01 at 21 55 12](https://user-images.githubusercontent.com/104775534/222251444-0847647e-971f-46a2-82dc-79805642aeae.png)

localhost/admin 

![Screenshot 2023-03-01 at 21 56 35](https://user-images.githubusercontent.com/104775534/222251771-429347ca-56d8-4796-a3c6-069a5d8be64e.png)



### Tehdään admin sivusto paremman näköiseksi

mennään taas settings.py tiedostoon

    cd
    cd publicwsgi/jeremco/jeremyco
    micro settings.py
    
Lisätään sinne import 

![Screenshot 2023-03-01 at 22 03 02](https://user-images.githubusercontent.com/104775534/222253088-e0ad85e6-406e-4f14-8632-6254afe334d5.png)

    cd .. 
    ./manage.py collectstatic
    
![Screenshot 2023-03-01 at 22 06 30](https://user-images.githubusercontent.com/104775534/222253822-7f35d5aa-3e04-408b-bc7a-2dd2f19f6370.png)

jotain mätää.. Mennään katsomaan settings.py ja BASE_DIR. Oletan, että BASE_DIR oli väärässä paikkaa (importin alla). Nyt näin: 

![Screenshot 2023-03-01 at 22 13 18](https://user-images.githubusercontent.com/104775534/222255169-6c10ee4c-452e-4de3-b9ef-cc3c3308fc26.png)

Tulos: 

![Screenshot 2023-03-01 at 22 13 53](https://user-images.githubusercontent.com/104775534/222255277-52e5eac5-9c5a-44eb-b427-55c504bdfe62.png)

![Screenshot 2023-03-01 at 22 14 09](https://user-images.githubusercontent.com/104775534/222255345-d63bf94b-f2c5-4e4d-a434-58e42d799c59.png)


### Kättelyt 

Aikaa meni 2 tuntia. Kivasti oppii kun pitää paljon kirjotella komentoja.

### Lähteet

https://terokarvinen.com/2022/deploy-django/, https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/
