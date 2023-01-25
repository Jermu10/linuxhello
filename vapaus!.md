# Tiistai 24.1.2023 19:30

## Tehtävä tiivistä vapaat lisenssit


### Free Software Definition

  https://www.gnu.org/philosophy/free-sw.html
  
Free Software Definition (FSD) on määritelmä joka määrittelee kriteerit sille, mitkä ohjelmat voidaan luokitella "vapaiksi ohjelmiiksi". FSD on julkaistu Free Software Foundation (FSF) organisaation toimesta. FSD keskittyy neljään päävapaukseen, jotka ohjelman käyttäjillä tulee olla:

- vapaus ajaa ohjelma haluamallaan tavalla
- vapaus tutkia ohjelman toimintaa ja muokata sitä
- vapaus jakaa kopioita ohjelmasta
- vapaus jakaa muokattuja versioita ohjelmasta

FSD:n mukaan ohjelma on vapaa, jos se antaa käyttäjille nämä neljä vapautta. FSD ei tarkoita että ohjelmisto olisi maksutonta tai että se ei voi olla kaupallinen.

### Open source licensing

http://lib.tkk.fi/Diss/2005/isbn9529187793/isbn9529187793.pdf

Open source licensing on lisenssi, joka antaa ihmisille oikeuden käyttää, muokata ja jakaa tiettyä ohjelmistoa. Useimmat open source -lisenssit ovat peräisin General Public License -perheestä, ja ne edellyttävät, että kaikki muokatut versiot ohjelmistosta julkaistaan avoimesti ja että ne ovat edelleen saatavilla avoimena lähdekoodina.


## Tehtävä a Kolmen ohjelman lisenssit

### HTOP

- Htop käyttää GNU General Public License v2.0 -lisenssiä.
- Löysin lisenssin ohjelman Github sivuilta: [https://github.com/htop-dev/htop](https://github.com/htop-dev/htop/blob/main/COPYING)
- Kyseessä on vapaa lisenssi!
- Lisenssin tärkeimmät oikeusvaatimukset ovat: 
  - Lähdekoodi on saatavilla kaikille
  - Ohjelmiston käyttäjät voivat muokata ja jakaa ohjelmistoa, mutta se pitää pitää GPL-lisenssin alaisena ja julkaistava avoimesti.


### GNU Wget

- Nimestä voi ehkä jo arvata eli Wget käyttää lisenssiä: GNU GENERAL PUBLIC LICENSE
- Löysin lisenssin GNU omilta sivuilta: https://www.gnu.org/software/wget/ 
  - Tarkempaa versiota ei sivuilla annettu 
- Kyseessä on vapaa lisenssi ja sama kuin HTOP:ssa


### Nmap
- Nmap käyttää GNU General Public License v2.0 -lisenssiä.
- Löysin lisenssin heidän omilta sivuiltaa: https://nmap.org/npsl/
- Kyseessä on vapaa lisenssi ja sama kuin HTOP:ssa

## Tehtävä b poimi txt tiedostosta tietoa käyttäen regexp

![Screenshot 2023-01-25 at 17 41 49](https://user-images.githubusercontent.com/104775534/214607933-c9bf54f9-bfdc-4f3e-982c-ecbbf79da1bd.png)

Tässä kolme komentoa:
- Ensimmäinen näyttää onko 'jaa' tiedostossa
- Toinen laskee montako 'jaa':ta tiedostossa on
- Kolmes näyttää kaikki kolmikirjaimiset sanat, jotka päättyvät kirjaimeen a


## Tehtävä c esimerkki pipestä

’cat | sort toimi.txt’ näyttää kaikki tiedoston rivit aakkosjärjestyksessä.

![Screenshot 2023-01-25 at 23 55 28](https://user-images.githubusercontent.com/104775534/214700291-f59e9af4-73f3-40cf-8022-949d10942eab.png)







