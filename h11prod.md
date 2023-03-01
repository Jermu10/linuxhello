# h11 - prod Keskiviikko 1.3.2023 klo 20.20

    Specs:

    Apple M1 Pro
    Cores 10
    Memory 16GB
    macOS Ventura 13.2


## a - Tee Djangon tuotantoasennus

### Alkutilanne localhost: 

![Screenshot 2023-03-01 at 20 25 42](https://user-images.githubusercontent.com/104775534/222229739-589d8840-fc26-42b2-b7ba-17c2d5d49a74.png)

### Seuraavaksi luodaan uudelle django sivustolle kansiot ja staattinen sivu

    mkdir -p publicwsgi/jeremyco/static/
    cd publicwsgi/jeremyco/static/
    micro index.html
    
### Seuraavaksi käydään luomassa conf tiedosto apache2/sites-available 

    cd /etc/apache2/sites-available/
    sudoedit jeremyco.conf
    
Kävin kopoimassa vanhasta conf tiedostosta mallin ja muutan siinä DocumentRootin oikeaksi Aliakseksi ja Directoryn oikeaksi:

![Screenshot 2023-03-01 at 20 42 20](https://user-images.githubusercontent.com/104775534/222234877-4b1e1967-a445-4886-8832-6de2696ce94b.png)

