##Vko 2 tehtävien dokumentointi

### Tehtävä asenna micro
22.1.2023 22:20
Aloitin komennoilla:

    sudo apt-get update
    
    sudo apt-get install micro
![Screenshot 2023-01-22 at 22 14 55](https://user-images.githubusercontent.com/104775534/213938624-95940776-64f5-42aa-aed0-80956995fef1.png)

Tämän jälkeen kokeilin toimiiko höskä. Kirjoitin terminaaliin:

    micro testi
micro aukesi ja pystyin testi tiedostoon kirjoittamaan testi.

### Tehtävä Listaa koneen rauta
  22.1.2023 22:35
  Aloitan kokeilemalla annettua komentoa.
![Screenshot 2023-01-22 at 22 35 05](https://user-images.githubusercontent.com/104775534/213939026-a93baa89-af3d-4776-a230-fa5df34cc372.png)

Lataan lshw:

    sudo apt-get install lshw
    
![Screenshot 2023-01-22 at 22 41 29](https://user-images.githubusercontent.com/104775534/213939316-cce2d1ca-0376-47eb-9714-d891101fa91e.png)
Tarkemmin en osaa analysoida. Selkeästi QEMU on virtuaali koneen tarjoaja ja sitä on tuolla vähän jokapaikassa sen takia..

### Tehtävä Asenna itsellesi kolme uutta komentoriviohjelmaa
22.1.2023 23:00

En oikein noita sovelluksia vielä tiedä niin googlettelin ja päädyin lataamaan tälläiset kolme:

    sudo apt-get install htop wget nmap -y
    
 ![Screenshot 2023-01-22 at 23 17 05](https://user-images.githubusercontent.com/104775534/213940916-b93b124e-73cb-4d52-b9cd-5c6fb5a975aa.png)
Tässä htop joka näyttää CPU ja memory usagen.


![Screenshot 2023-01-22 at 23 24 05](https://user-images.githubusercontent.com/104775534/213941199-a690fc91-c167-4167-95c8-60506860df1a.png)
wgetillä voi ladata netistä suoraan omaan kirjastoon. Tällä komennolla sain tämän kyseisen tiedoston suoraan ladattua.

    wget https://github.com/Jermu10/linuxhello/blob/main/komentajaPingviini.md
    
    
 
   nmap pystyy scannaa verkon ja tarkistamaa avoimet portit, käynnissä olevat palvelut jne.
   ![Screenshot 2023-01-22 at 23 27 59](https://user-images.githubusercontent.com/104775534/213941352-f7fe4fed-c86f-449a-bed2-e1d5769a7596.png)


 
## Tehtävä FHS 23:35
En nyt ollut varma riittääkö kuvat kun on listattu kunkin paikan asiat ja pieni selostus. 

Tässä aloitan rootissa jonka alla on kaikki. Homessa on kaikki käyttäjät. Käyttäjässä (Jeremy) on käyttäjän oma tiedosto minne kyseinen käyttäjä voi tallentaa dataa.
![Screenshot 2023-01-22 at 23 45 09](https://user-images.githubusercontent.com/104775534/213942042-e00908bb-9225-4317-bb7e-fb76129e5d95.png)



etc- hakemistossa on kaikkia järjestelmän hallintaan liittyviä asetustiedostoja. Nämä tiedostot määrittelevät kuinka järjestelmä toimii ja miten se on asennettu.
![Screenshot 2023-01-22 at 23 47 56](https://user-images.githubusercontent.com/104775534/213942144-c4953281-50f6-4d15-a1b9-c342df562b10.png)

Mediassa näkyy kaikki ulkoiset asemat. Kuten levyasemat ja usb-asemat.
![Screenshot 2023-01-22 at 23 53 51](https://user-images.githubusercontent.com/104775534/213942350-5b753710-e07b-4034-b1e8-bc176f9e665c.png)

var/log sisältää erilaisia lokitiedostoja, jotka kirjaavat erilaisia tapahtumia järjestelmässä. Nämä tiedostot auttavat seuraamaan ja diagnosoimaan ongelmia järjestelmässä. Esimerkiksi tiedostot kuten /var/log/auth.log sisältävät tietoja kirjautumisyrityksistä.

![Screenshot 2023-01-22 at 23 57 15](https://user-images.githubusercontent.com/104775534/213942475-9f9b3e81-5a4d-4be1-98ed-3da811061f57.png)


## Tehtävä näytä 2 kuvaavaa esimerkkiä grep-komennon käytöstä

Tässä etsitään tiedostosta kyseinen sana.
![Screenshot 2023-01-23 at 0 05 34](https://user-images.githubusercontent.com/104775534/213942820-09c0a8b2-05d0-4f3d-8974-5f260eb922e8.png)

Tässä tulostaa millä rivillä kyseinen sana on.
![Screenshot 2023-01-23 at 0 16 41](https://user-images.githubusercontent.com/104775534/213943268-faa1bf93-a14c-43a7-a863-591aad1fe73d.png)

