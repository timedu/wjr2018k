---
layout: exercise_page
title: "Tehtävä 4.6: Puhelinmuistio: Firebase (3p)"
exercise_template_name: W4E06.PuhFirebase
exercise_discussion_id: 99285
exercise_upload_id: 382326
modified_at: 21.4.2018
---


Täydennä hieman keskeneräiseksi jäänyttä puhelinmuistiosovellusta, joka on ulkoiselta käyttäytymiseltään pääosin [Tehtävän 4.4](../tehtava44) ratkaisun kaltainen. Laadittava sovellus kuitenkin tukeutuu tietojen talletuksen osalta [Firebase-tietokantaan][firebase-db]. Sovelluksen käyttö myös edellyttää käyttäjältään tunnistautumista, mikä toteteutetaan [Firebasen autentikointipalvelulla][firebase-auth].

[firebase-db]: https://firebase.google.com/docs/database/
[firebase-auth]: https://firebase.google.com/docs/auth/

Sovelluksen ulkoasu ja reititys on pääosin kuten [Tehtävässä 4.4](../tehtava44), mutta tunnistautumisvaatimus kuitenkin tuo näihin pieniä muutoksia.

![ui-1](../img/w4e06-ui-1.png "ui-1"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 1. Hae numeroita -sivu: ei kirjauduttu.</small>


Jos käyttäjä ei ole kirjautunut, *Hae numeroita* -sivulla on *login* -painike. Tällöin *Nimi* -kenttään ei voi kirjoittaa (Kuva 1). Käyttäjä tunnistautuu klikkaamalla *login* -painiketta. Jos tunnistautuminen onnistuu, näkymään ilmestyy *login* -painikkeen tilalle *logout* -painike ja *Nimi* -kenttä aktivoituu (Kuva 2). *logout* -painikkeen klikkaus palauttaa näkymän Kuvassa 1 esitetyn kaltaiseksi.


![ui-2](../img/w4e06-ui-2.png "ui-2"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 2. Hae numeroita -sivu: kirjauduttu.</small>


 Kun sivun tekstikenttään kirjoitetaan hakuehto,  sivulle ilmestyy *find* -painike (Kuva 3).


![ui-3](../img/w4e06-ui-3.png "ui-3"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 3. Hae numeroita -sivu: hakukenttä täytetty.</small>


Kun *find* -painiketta klikataan, sivulle ilmestyy hakuehdoksi annetun henkilön puhelinnumerot, joiden ohessa on *poista*-linkit. Numeroluettelon alapuolella on *uusi numero* -linkki (Kuva 4). Linkkien klikkaus vie vastaaville sivuille (*Kuvat 5 ja 6*). Nämä sivut ovat ulkoasultaan samanlaisia kuin [Tehtävän 4.4](../tehtava44) vastaavat.

![ui-4](../img/w4e06-ui-4.png "ui-4"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 4. Hae numeroita -sivu: haku suoritettu.</small>



![ui-5](../img/w4e06-ui-5.png "ui-5"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 5. Lisää numero -sivu.</small>



![ui-6](../img/w4e06-ui-6.png "ui-6"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 6. Poistetaanko numero -sivu.</small>

Kun käyttäjä on kirjautunut, sovelluksen näkymiin voidaan siirtyä painikkeiden ja linkkien ohella myös suorilla osoitteilla (vrt. [Tehtävä 4.4](../tehtava44)). Jos kirjautumista ei ole tehty, on suoralla osoitteella pääsy ainoastaan sovelluksen juuriosoitteeseen (`/W4E06/#!/` tai `/W4E06/`), joka tuo esiin *Hae numeroita* -näkymän. Yritys muuhun osoitteeseen (esim. `/W4E06/#/bart`, `/W4E06/#!/bart/remove/111` tai `/W4E06/#!/jotakin/muuta`) palauttaa käsittelyn juuriosoitteeseen.


[Firebase-tietokanta][firebase-db] on avain-arvo -tyyppinen, missä arvo voi edelleen muodostua  avain-arvo -pareista. Tässä tietokannan rakenne näkyy Firebase-konsolissa seuraavanlaisesti:


![db](../img/w4e06-db.png "db"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 7. Tietokanta.</small>


Firebase-projektin autentikonti-asetuksiin liittyvä sivu tulee esiin konsolin valikon *Authentication* -valinnalla. *SIGN-IN METHOD* -välilehdellä voi valita projektissa käytettävät tunnistusmenetelmät. Tässä käytetään *Email/Password* -tunnistusta.  Tunnistetiedot voi määritellä *USERS* -välilehdellä. *Email* -arvon ei tarvitse tässä olla oikea sähköpostiosoite.

Tietokantaan liittyvät tunnistautumissäännöt määritellään Firebase -konsolin *Database* -sivun *RULES* -välilehdellä. Seuraavanlaisilla tässä käytettävillä säännöillä tietojen sekä lukeminen että kirjoittaminen edellyttää tunnistautumista:


![db](../img/w4e06-auth.png "db"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 8. Tietokantaan liittyvät tunnistautumissäännöt.</small>


Seuraavassa on pääsivun (`index.html`) `body`-elementin merkkaus.

{% highlight html %}

    <body ng-app="PuhApp">

        <h1>Puhelinmuistio</h1>
        <div ng-view></div>
        ...

        <script src="js/PuhAppModule.js"></script>        
        <script src="js/RemoveController.js"></script>
        <script src="js/wjr-btn.js"></script>
                
        <script src="todo/PuhController.js"></script>
        <script src="todo/AddController.js"></script>
        
    </body>

{% endhighlight %}

<small>Listaus 1. Sovelluksen pääsivun *body* -elementin merkkaus.</small>

Sovellukseen liittyy  viisi JavaScript -tiedostoa, joista palautetaan `todo`-kansiossa olevat *Hae numeroita* - ja *Lisää numero* -sivuihin liittyvät kontrollerit `PuhController.js` ja `AddController.js`. Näihin laadittavan koodin lisäksi tiedostoon `PuhAppModule.js` tulee määritellä Firebase-projektiin liittyvät tunnisteet. Tiedoston `wjr-btn.js` (direktiivi) voi kopioida [Tehtävän 4.4](../tehtava44) ratkaisusta.

Projektiin kuuluu myös kolme templatea, joista kaksi `view`-kansiossa olevaa on pohjassa valmiina. `todo`-kansion `search.html` edellyttää täydennyksiä: elemettien aktiivisuus ja näkyvyys sekä autentikointiin liittyvien metodien kutsut. Pohjassa oleva tiedosto `PuhAppModule.js` määrittelee näkyvyysalueelle kirjautumiseen liittyvät funktiot `singIn` ja `signOut` sekä boolean-tyyppisen muuttujan `signedIn`, joiden käyttöä tehtävän tämän osan ratkaisu edellyttänee. Myös direktiiveistä [ng-disabled][ng-disabled], [ng-hide][ng-hide] ja  [ng-show][ng-show] saattaa olla tässä hyötyä.

[ng-disabled]: https://docs.angularjs.org/api/ng/directive/ngDisabled
[ng-hide]: https://docs.angularjs.org/api/ng/directive/ngHide
[ng-show]: https://docs.angularjs.org/api/ng/directive/ngShow


`PuhAppModule.js` sisältää myös palvelun (funktion) `Puh`, jonka kutsu palauttaa henkilön numeroluetteloa vastaavan AngularFire-rajapinnan tarjoaman [$firebaseArray][firebaseArray]-objektin. Pohjassa valmiina oleva `RemoveController.js` käyttää objektin `$remove`- ja `$getRecord`-metodeja. Tehtävässä laadittava `AddController.js` edellyttänee `$add`-metodin käyttöä.

[firebaseArray]: https://github.com/firebase/angularfire/blob/master/docs/reference.md#firebasearray


**Palauta** tehtävän ratkaisusta tiedostot `PuhController.js`, `AddController.js` ja `search.html`, joiden rungot löytyvät tehtäväkohjan `todo`-kansiosta. Varmista ennen palautusta, että sovellus toimii odotetusti. Varmista myös, että selaimen konsolille ei tule virheilmoituksia sovellusta käytettäessä.

### Lisätietoja

[Firebase -dokumentaatio](https://firebase.google.com/docs/)   
[AngularFire API Reference](https://github.com/firebase/angularfire/blob/master/docs/reference.md)     
[AngularFire Guide](https://github.com/firebase/angularfire/blob/master/docs/guide/README.md)   
