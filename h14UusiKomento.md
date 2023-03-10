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
    
![Screenshot 2023-03-10 at 20 32 37](https://user-images.githubusercontent.com/104775534/224396290-5fbcba0f-9dd5-45e4-845e-5bc8cdf19506.png)

Testataan erittäin vakuuttavalla testillä(rämpyttämällä), että ohjelma toimii: 

![Screenshot 2023-03-10 at 20 34 04](https://user-images.githubusercontent.com/104775534/224396758-a35d0139-1931-4a71-a7bb-eda01c337560.png)

Toimii, mutta vähän liikaa vettä omaan makuun..

### Seuraavaksi lisätään tiedostolle oikeudet, että sitä voi kaikki suorittaa 

    chmod ugo+x mitajuodaan #user,group,other annetaan x = execute luvat
    ls -l mitajuodaan
    
![Screenshot 2023-03-10 at 20 36 44](https://user-images.githubusercontent.com/104775534/224397566-769c6572-db55-4e36-9a22-80aaa1992604.png)

### Seuraavaksi kopioidaan tiedosto /usr/local/bin hakemistoon, jonka jälkeen kaikki käyttäjät voivat käyttää komentoa

    sudo cp mitajuodaan /usr/local/bin



