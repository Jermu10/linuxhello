# 26.2.2023 

## a - tee oma tietokantasovellus 22:30

Aloitetaan lataamalla virtualenv, joka on python kehitysympäristö

    sudo apt-get update
    sudo apt-get install virtualenv
    
Seuraavaksi luodaan env niminen ympäristö

    virtualenv --system-site-packages -p python3 env/
    
--system-site-packages = ympäristössä käytetään globaalia python-asennusta ja sen kirjostoja
-p python3 = Määrittää pythonin version3 ympäristöön

Seuraavaksi aktivoidaan luomamme env/ ympäristö

    source env/bin/activate
    
Komennon jälkeen alkuun tuli env/

![Screenshot 2023-02-26 at 22 51 56](https://user-images.githubusercontent.com/104775534/221436565-e90887eb-dab8-4e4d-a5b2-086a58bd0709.png)

Seuraavaksi luodaan tekstitiedosto, joka kertoo, että haluamme "django" nimisen python-paketin
Luodaan requirements.txt jonka sisään kirjoitetaan "django" ja tarkastetaan, että meni oikein

    micro requirements.txt
    cat requirements.txt
    
tulos: 
    
![Screenshot 2023-02-26 at 22 58 56](https://user-images.githubusercontent.com/104775534/221436943-9b373fc2-49f6-4995-9a44-d0c947fc991a.png)

Seuraavaksi lisätään requirements.txt ympäristöömme ja tarkistetaan django versio

    pip install -r requirements.txt
    django-admin --version
    
Tulos: 

![Screenshot 2023-02-26 at 23 02 14](https://user-images.githubusercontent.com/104775534/221437095-c4d31aa3-74ee-4a66-bf16-680c4613a8ab.png)

Seuraavaksi luodaan django-projekti ja käynnistetään se!

    django-admin startproject garden
    cd garden
    ./manage.py runserver
    
tulos konsolista ja portista http://127.0.0.1:8000/: 
    
![Screenshot 2023-02-26 at 23 09 09](https://user-images.githubusercontent.com/104775534/221437430-bf68fbdd-33be-4504-9828-d8d3f763dd40.png)

![Screenshot 2023-02-26 at 23 09 53](https://user-images.githubusercontent.com/104775534/221437469-c954717a-8286-4928-9e5f-87061ef04d8e.png)

Seuraavaksi päivitetään databaset, jotta voidaan luoda käyttäjä sivulle

      ./manage.py makemigrations
      ./manage.py migrate

tulos: ./manage.py makemigrations tuli vastaus "no changes detected".
./manage.py migrate: 

![Screenshot 2023-02-26 at 23 20 38](https://user-images.githubusercontent.com/104775534/221437942-c12a4b33-0f28-4079-a58e-ef25a447048d.png)

![Screenshot 2023-02-26 at 23 21 54](https://user-images.githubusercontent.com/104775534/221438004-c6650976-bdb7-4ee1-b969-5009f7a1abe7.png)

Seuraavaksi luodaan "superkäyttäjä", jolla voidaan kirjautua sisään

    ./manage.py createsuperuser
    
tulos: 

![Screenshot 2023-02-26 at 23 34 00](https://user-images.githubusercontent.com/104775534/221438684-f9295903-6b01-49bf-b844-595aa04097fb.png)

Luodaan käyttäjä sivun 





