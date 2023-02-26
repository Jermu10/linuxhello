# 26.2.2023 

## a - tee oma tietokantasovellus 22:30

### Aloitetaan lataamalla virtualenv, joka on python kehitysympäristö

    sudo apt-get update
    sudo apt-get install virtualenv
    
### Seuraavaksi luodaan env niminen ympäristö

    virtualenv --system-site-packages -p python3 env/
    
--system-site-packages = ympäristössä käytetään globaalia python-asennusta ja sen kirjostoja

-p python3 = Määrittää pythonin version3 ympäristöön

### Seuraavaksi aktivoidaan luomamme env/ ympäristö

    source env/bin/activate
    
Komennon jälkeen alkuun tuli env/

![Screenshot 2023-02-26 at 22 51 56](https://user-images.githubusercontent.com/104775534/221436565-e90887eb-dab8-4e4d-a5b2-086a58bd0709.png)

### Seuraavaksi luodaan tekstitiedosto, joka kertoo, että haluamme "django" nimisen python-paketin
Luodaan requirements.txt jonka sisään kirjoitetaan "django" ja tarkastetaan, että meni oikein

    micro requirements.txt
    cat requirements.txt
    
tulos: 
    
![Screenshot 2023-02-26 at 22 58 56](https://user-images.githubusercontent.com/104775534/221436943-9b373fc2-49f6-4995-9a44-d0c947fc991a.png)

### Seuraavaksi lisätään requirements.txt ympäristöömme ja tarkistetaan django versio

    pip install -r requirements.txt
    django-admin --version
    
Tulos: 

![Screenshot 2023-02-26 at 23 02 14](https://user-images.githubusercontent.com/104775534/221437095-c4d31aa3-74ee-4a66-bf16-680c4613a8ab.png)

### Seuraavaksi luodaan django-projekti ja käynnistetään se!

    django-admin startproject garden
    cd garden
    ./manage.py runserver
    
tulos konsolista ja portista http://127.0.0.1:8000/: 
    
![Screenshot 2023-02-26 at 23 09 09](https://user-images.githubusercontent.com/104775534/221437430-bf68fbdd-33be-4504-9828-d8d3f763dd40.png)

![Screenshot 2023-02-26 at 23 09 53](https://user-images.githubusercontent.com/104775534/221437469-c954717a-8286-4928-9e5f-87061ef04d8e.png)

### Seuraavaksi päivitetään databaset, jotta voidaan luoda käyttäjä sivulle

      ./manage.py makemigrations
      ./manage.py migrate

tulos: ./manage.py makemigrations tuli vastaus "no changes detected".
./manage.py migrate: 

![Screenshot 2023-02-26 at 23 20 38](https://user-images.githubusercontent.com/104775534/221437942-c12a4b33-0f28-4079-a58e-ef25a447048d.png)

![Screenshot 2023-02-26 at 23 21 54](https://user-images.githubusercontent.com/104775534/221438004-c6650976-bdb7-4ee1-b969-5009f7a1abe7.png)

### Seuraavaksi luodaan "superkäyttäjä", jolla voidaan kirjautua sisään

    ./manage.py createsuperuser
    
tulos: 

![Screenshot 2023-02-26 at 23 34 00](https://user-images.githubusercontent.com/104775534/221438684-f9295903-6b01-49bf-b844-595aa04097fb.png)

### Luodaan käyttäjä sivun "users     add" kohdasta


Valitaan uudelle käyttäjälle staff- ja superuser-statukset

![Screenshot 2023-02-26 at 23 37 36](https://user-images.githubusercontent.com/104775534/221438903-d472cd3b-c0c9-4c58-a173-a7db8c77b866.png)

TULOS! Kirjaudutaan uudella käyttäjällä: 

![Screenshot 2023-02-26 at 23 39 41](https://user-images.githubusercontent.com/104775534/221439041-791ff31a-a81a-43a8-a63d-a722ff1bc1b7.png)

## Luodaan Database

Luodaan uusi "sovellus" nimeltä mbg (MyBackGarden)

    ./manage.py startapp mbg
    
lisätään mbg ympäristöön: INSTALLED_APPS = ['mbg',]

        micro garden/settings.py 

![Screenshot 2023-02-27 at 0 09 07](https://user-images.githubusercontent.com/104775534/221440413-f7a74243-25ba-4111-b3f1-bf7095bd9624.png)

### Seuraavaksi luodaan scripti, jolla django luo automaattisesti databasen

        micro mbg/models.py
        
![Screenshot 2023-02-27 at 0 13 15](https://user-images.githubusercontent.com/104775534/221440591-12f0e9ee-bd05-4194-84ca-4cab9352feac.png)

Seuraavaksi päivitetään databaset, jossa pitäisi näkyä mbg

        ./manage.py makemigrations
        ./manage.py migrate
        
tulos: 

![Screenshot 2023-02-27 at 0 16 50](https://user-images.githubusercontent.com/104775534/221440763-72ca5ebc-7e5e-43a5-ad85-d3ee77a92051.png)

![Screenshot 2023-02-27 at 0 17 27](https://user-images.githubusercontent.com/104775534/221440787-ff954510-aaf0-4e11-a9cc-2360fdca8702.png)
    
Jotta voidaan nähdä admin sivulla databasemme, se pitää rekistörödä sinne

    micro mbg/admin.py
    
![Screenshot 2023-02-27 at 0 20 48](https://user-images.githubusercontent.com/104775534/221440928-4112174e-3366-40f6-a3a6-eadfc42645da.png)

        
Mennään katsomaan tulos

    ./manage.py runserver
    
Tulos: 

![Screenshot 2023-02-27 at 0 22 21](https://user-images.githubusercontent.com/104775534/221441017-f574146d-5240-4f7c-926f-e5544d023540.png)

Kokeillaan luoda, muokata ja poistaa hedelmä nettisivulla:

Lisäys: ![Screenshot 2023-02-27 at 0 23 36](https://user-images.githubusercontent.com/104775534/221441077-c7247fbc-728f-4297-9575-5b2889034b5e.png)

Muokkaus: ![Screenshot 2023-02-27 at 0 24 18](https://user-images.githubusercontent.com/104775534/221441106-27085a2e-03b5-440e-87f6-5f0f27684a22.png)

Poisto: ![Screenshot 2023-02-27 at 0 24 38](https://user-images.githubusercontent.com/104775534/221441120-c320ae21-18cc-4a07-8fba-6dedcfde1731.png)

## Vaihdetaan vielä, että nimet näkyvät

    micro mbg/models.py
    
Lisätään maalatut scriptit:

![Screenshot 2023-02-27 at 0 30 07](https://user-images.githubusercontent.com/104775534/221441369-436d446d-99db-480b-a07f-34a2a8f68194.png)

Tulos: 

![Screenshot 2023-02-27 at 0 30 57](https://user-images.githubusercontent.com/104775534/221441405-55263c11-5a79-45e3-af45-04a72248e05a.png)



## Kättelyt 00.30

Rennosti tehdessä aikaa kului 2 tuntia. Ihan hyvin meni siihen nähden, etten viime tunnille päässyt.

## Lähteet

https://terokarvinen.com/2022/django-instant-crm-tutorial/ , https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/ , https://docs.djangoproject.com/en/4.1/topics/db/examples/many_to_one/

