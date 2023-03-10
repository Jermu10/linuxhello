# h14 - Uusi komento Perjantai 10.3.2023 19:30


## a - Tee uusi linux komento Bashilla

### Alkutilanne 

![Screenshot 2023-03-10 at 20 10 59](https://user-images.githubusercontent.com/104775534/224391857-5e47c8e3-ebe9-4fee-b7c3-7f5cc757f741.png)


Aloitetaan luomalla tiedosto jonka sisään kirjoitetaan bash komento

    micro kerropaiva
    
![Screenshot 2023-03-10 at 20 01 05](https://user-images.githubusercontent.com/104775534/224390050-70fcb7c6-1d96-42fb-8140-94b09286581e.png)

### Seuraavaksi annetaan kaikille käyttäjäryhmille oikeudety ajaa tiedosto kerropaiva

    chmod ugo+x kerropaiva #user,group,other annetaan x = execute luvat
    ls -l kerropaiva

![Screenshot 2023-03-10 at 20 03 52](https://user-images.githubusercontent.com/104775534/224390507-2a085ae5-bfe1-44a2-9ecc-625cfae9eff7.png)

### Seuraavaksi kopioidaan tiedosto /usr/local/bin hakemistoon, jonka jälkeen kaikki käyttäjät voivat käyttää komentoa

    sudo cp kerropaiva /usr/local/bin
    
TULOS: 

![Screenshot 2023-03-10 at 20 08 30](https://user-images.githubusercontent.com/104775534/224391364-2200f06a-b57b-46d0-8a55-b5dd87652781.png)

![Screenshot 2023-03-10 at 20 08 44](https://user-images.githubusercontent.com/104775534/224391411-173cfec7-80e0-4cd1-a266-07e1f0c626a0.png)

## b - luodaan python3 komento

Perjantain kunniaksi annan sattuman valita illan juomani.

    micro mitajuodaan
    
![Screenshot 2023-03-10 at 20 44 57](https://user-images.githubusercontent.com/104775534/224399741-f76dedb7-f9bf-4393-a971-627cd8ba2a90.png)


Testataan erittäin vakuuttavalla testillä(rämpyttämällä), että ohjelma toimii: 

![Screenshot 2023-03-10 at 20 34 04](https://user-images.githubusercontent.com/104775534/224396758-a35d0139-1931-4a71-a7bb-eda01c337560.png)

Toimii, mutta vähän liikaa vettä omaan makuun..

### Seuraavaksi lisätään tiedostolle oikeudet, että sitä voi kaikki suorittaa 

    chmod ugo+x mitajuodaan #user,group,other annetaan x = execute luvat
    ls -l mitajuodaan
    
![Screenshot 2023-03-10 at 20 36 44](https://user-images.githubusercontent.com/104775534/224397566-769c6572-db55-4e36-9a22-80aaa1992604.png)

### Seuraavaksi kopioidaan tiedosto /usr/local/bin hakemistoon, jonka jälkeen kaikki käyttäjät voivat käyttää komentoa

    sudo cp mitajuodaan /usr/local/bin

TULOS: 

![Screenshot 2023-03-10 at 20 47 08](https://user-images.githubusercontent.com/104775534/224400136-c5d2479e-52d3-495d-a5d0-3d0a089aa503.png)


![Screenshot 2023-03-10 at 20 46 08](https://user-images.githubusercontent.com/104775534/224399951-aee77302-b5f6-4ee7-b3c9-2bc1fb869d5f.png)



## c - luo komento, joka tekee jotain monelle tiedostolle

Tehdään tällänen .txt tiedostojen poistaja ruletti

![Screenshot 2023-03-10 at 21 51 37](https://user-images.githubusercontent.com/104775534/224414407-aeb72c9e-ddcc-45c7-ac21-d086100f4dc3.png)

Testataan, että toimii

![Screenshot 2023-03-10 at 21 32 25](https://user-images.githubusercontent.com/104775534/224410873-113fbc27-910b-46cd-a9fa-62870e07b529.png)

Testataan myös varmuudenvuoksi tämä:

![Screenshot 2023-03-10 at 21 36 21](https://user-images.githubusercontent.com/104775534/224411568-bfd3a74c-b473-4b00-bcfb-eeea847199b7.png)

### Seuraavaksi annetaan kaikille käyttäjäryhmille oikeudety ajaa tiedosto kerropaiva

    chmod ugo+x ruletti #user,group,other annetaan x = execute luvat
    ls -l ruletti
    

### Seuraavaksi kopioidaan tiedosto /usr/local/bin hakemistoon, jonka jälkeen kaikki käyttäjät voivat käyttää komentoa

    sudo cp mitajuodaan /usr/local/bin

TULOS:

![Screenshot 2023-03-10 at 21 54 32](https://user-images.githubusercontent.com/104775534/224414907-47ca3277-fc34-4d71-b45d-6b2637d11148.png)

![Screenshot 2023-03-10 at 21 55 47](https://user-images.githubusercontent.com/104775534/224415125-56eb7fc0-17b7-4262-b44a-a6bca0e7b788.png)





