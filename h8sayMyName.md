# h8 - Say my name Perjantai 10.2.2023 18:45

    Specs:
    Apple M1 Pro
    Cores 10
    Memory 16GB
    macOS Ventura 13.2
    
    
## a - Vuokraa domainnimi ja aseta se virtuaalipalvelimeesi

Päätin vuokrata parikin nimeä Namecheap-palvelusta: drinkkilinkki.com ja åström.org
Ostoskorissa valitaan haluatko auto-renewin päälle ja moneksi vuodeksi.
Domain privacyn pidän päällä. PremiumDNS ei tarvitse.
Muita lisäpalveluita en ota, koska en niitä tarvitse.
åström.org domain registration näyttää epäilyttävältä, mutta kokeillaan..



![Screenshot 2023-02-10 at 18 55 17](https://user-images.githubusercontent.com/104775534/218150163-60f0cb0a-d4e4-46b7-ad6c-47aa482ef444.png)

Sitten rekistöröidyttiin ja täällä tuli tästä äskeisestä ihmetyksestä lisäkyselyä: UPDATE: åström.orgia ei pystynyt ostamaan: IDN language Finnish is not supported. Mietin tossa, että Swedish on tuettuna, niin näppäimistöhän heillä on sama.

![Screenshot 2023-02-10 at 19 01 28](https://user-images.githubusercontent.com/104775534/218151673-fa2e352c-12a0-4d62-af8d-9e7af9b1023e.png)

Valitsin tuohon language Finnish ja painoin Continue.
"Unicode on tietokonejärjestelmiä varten kehitetty merkistöstandardi ja käytännössä sama kuin yleismaailmallisen merkistön määrittävä kansainvälinen standardi ISO/IEC 10646." -Wikipedia https://fi.wikipedia.org/wiki/Unicode
"Punycode on esitys Unicodesta, jossa on rajoitettu ASCII-merkkiosajoukko" -Wikipedia https://en.wikipedia.org/wiki/Punycode


Valitaan maksutapa ja Continue..
Näköjään, jos valitsee, että ottaa kolmen vuoden diilin, ei pääse maksamaan kerran vuodessa vuotta pois, vaan heti maksaa kaikki kolme vuotta.

Sitten mennään domainin asetuksiin ja Advanced DNS. Siellä Laitetaan oman virtuaalipalvelimen IP-osoite oikeaan URL.


![Screenshot 2023-02-10 at 19 21 45](https://user-images.githubusercontent.com/104775534/218155771-68a16f24-1724-4ca2-9b0b-3cfd667fab9e.png)

Ensiki valitaan A Record, sitten Host @ tarkoittaa URL pelkästään ja ip osoite, minne haluat urlin johtavan. 


![Screenshot 2023-02-10 at 19 23 41](https://user-images.githubusercontent.com/104775534/218156161-a056dbcb-e8ed-4a2a-be2e-8f5d3334638a.png)

Sitten tehtiin vielä toinen, jossa pääsee nettisivulle, jos kirjoittaa urlin alkuun www.
Lopuksi vielä vaihetaan molempien TTL Automaticita 5 minuuttiin. 

Jostain syystä @ sivu ei näy ja tulee 404, mutta wwww näkyy. 
Kokeiltu Safarilla sekä Chromella.

Jostain syystä @ väärä osoitekkin..

![Screenshot 2023-02-10 at 19 36 39](https://user-images.githubusercontent.com/104775534/218158613-18db4aab-fdff-480a-b87e-6c3b82a132f7.png)

![Screenshot 2023-02-10 at 19 37 06](https://user-images.githubusercontent.com/104775534/218158700-06461732-fd58-440c-ac0e-9650027601a7.png)

Kokeillaan tehdä uusi @ record. EI TOIMI.

## 19:40 b - Tutki oman nimesi tietoja 'host' ja 'dig' komennoilla

Kirjaudutaan ssh:n avulla virtuaalipalvelimelle ja kokeillaan host komennolla mitä näkyy.

    ssh severi@IP-osoite
    host www.drinkkilinkki.fi
    host drinkkilinkki.fi
  
![Screenshot 2023-02-10 at 19 47 40](https://user-images.githubusercontent.com/104775534/218160644-3c285652-2315-427e-8d50-2e082cd0140e.png)

Täällä kyllä näkyy oikea IP-osoite..

![Screenshot 2023-02-10 at 19 48 09](https://user-images.githubusercontent.com/104775534/218160738-6505cf9f-f6df-4d6f-9221-2f483fc500e5.png)


Asennetaan dig: 

    sudo apt-get update
    sudo apt install dig

Kokeillaan molemmat sivut:

    dig drinkkilinkki.com

![Screenshot 2023-02-10 at 19 54 45](https://user-images.githubusercontent.com/104775534/218162001-48803126-ec61-4f19-b2cd-316a7b953219.png)

    dig www drinkkilinkki.com

![Screenshot 2023-02-10 at 19 55 12](https://user-images.githubusercontent.com/104775534/218162071-163ee1db-5a38-40cb-bc27-b59bd795b6cc.png)

