# H13 - Hello World! Keskiviikko 8.3.2023 klo: 11.20

## a - Käännä "Hei maailma" kolmella kielellä

    Hei maailma!
    Englanniksi = Hello world!
    Ruotsiksi = Hej världen!
    Espanjaksi = Hola Mundo!
    
Noniin vitsit sikseen aloitetaan.

### Python3

Tarkistin aluksi, että löytyyhän masiinasta Python3
  
        python3 --version # löytyy!
        
Luodaan kansio, johon laitetaan nämä ohjelmat

    mkdir huvipuisto
    cd huvipuisto
    micro helloworld.py

Kirjoitetaan tiedostoon

![Screenshot 2023-03-08 at 11 32 06](https://user-images.githubusercontent.com/104775534/223675965-01d5f9ed-a36c-42bd-87c9-fec359261800.png)

"Juostaan/suoritetaan/runnataan" ohjelma komennolla

        python3 helloworld.py

![Screenshot 2023-03-08 at 11 33 09](https://user-images.githubusercontent.com/104775534/223676196-07fa6eb9-0c56-41d4-9a0b-eb1e1e19da6f.png)


### Bash

    micro helloworld.txt
    
![Screenshot 2023-03-08 at 11 37 32](https://user-images.githubusercontent.com/104775534/223677176-9980ebfe-c1cc-4836-94e4-46d66a729fea.png)

Juostaan
    
    bash --version # löytyy!
    bash helloworld.txt
    
![Screenshot 2023-03-08 at 11 38 48](https://user-images.githubusercontent.com/104775534/223677461-2d437de7-e84e-40bb-a744-d3743e892353.png)

    
### Ruby

    
    ruby --version  # ei ollu, pitää asentaa
    sudo apt-get update
    sudo apt-get install ruby-full # katsottu ruby-land.org
    ruby --version
    
![Screenshot 2023-03-08 at 11 42 54](https://user-images.githubusercontent.com/104775534/223678398-cf4018de-ea61-482f-ad46-adba9b3383e1.png)

    cd
    cd huvipuisto
    micro helloworld.rb
    
![Screenshot 2023-03-08 at 11 43 47](https://user-images.githubusercontent.com/104775534/223678608-0e9777ee-3d7b-489f-bd01-18b7030853d8.png)

Juostaan

    ruby helloworld.rb
    
![Screenshot 2023-03-08 at 11 44 32](https://user-images.githubusercontent.com/104775534/223678777-e0436200-0c32-4ddf-b51a-4a7651d83c0f.png)


## b - Tee greetme: ohjelma joka tervehtii käyttäjää. Lähde: https://chat.openai.com/chat

    cd
    cd huvipuisto
    micro hellouser.py
    
![Screenshot 2023-03-08 at 12 07 57](https://user-images.githubusercontent.com/104775534/223684380-bb32aef6-eb6c-4833-b76e-c0097b5a698c.png)

TULOS: 

![Screenshot 2023-03-08 at 12 08 25](https://user-images.githubusercontent.com/104775534/223684485-e4658fa8-ef76-482d-a9e4-80133db8fdc2.png)

![Screenshot 2023-03-08 at 12 08 37](https://user-images.githubusercontent.com/104775534/223684525-261d13fb-58c6-4387-9dd0-6a83813850ec.png)

## KÄTTELYT

Aikaa kului 40min. Kivaa oli.

## LÄHTEET

- https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/
- https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/
- https://www.ruby-lang.org/en/documentation/installation/





