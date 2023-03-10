# h14 - Uusi komento Perjantai 10.3.2023 19:30


## a - Tee uusi linux komento Bashilla

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



