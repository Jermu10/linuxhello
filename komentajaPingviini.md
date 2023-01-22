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


 


