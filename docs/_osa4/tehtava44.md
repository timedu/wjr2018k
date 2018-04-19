---
layout: exercise_page
title: "Tehtävä 4.4: Puhelinmuistio: Routing (3p)"
exercise_template_name: W4E04.PuhRouting
exercise_discussion_id: 99283 
exercise_upload_id: 382324
modified_at: 19.4.2018
---


Kehitä puhelinmuistio-sovellusta edelleen siten, että se muodostuu käyttäjän näkökulmasta kolmesta erillisestä sivusta (Kuvat 1-3).

![ui-1](../img/w4e04-1.png "ui-1"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}


<small>Kuva 1. Numeroiden haku.</small>

*Hae numeroita* -sivu on sovelluksen oletusnäkymä, joka tulee näkyviin tentäessä (kehitysympäristössä) pyyntö osoitteeseen `http://localhost:8383/W4E04/`[^1]. Sivulle päädytään myös esim. pyynnöllä `http://localhost:8383/W4E04/#!/bart`, jolloin `Nimi`-kenttään on valmiiksi täytetty henkilö `bart` ja sivulla on esillä kaikki em. henkilölle talletetut puhelinnumerot (vrt. Kuva 1). Sivulla olevien `uusi numero`- ja `poista` -linkkien avulla voidaan siirtyä sovelluksen muille sivuille. *Lisää numero* -sivulle voidaan siirtyä vain, jos `Nimi`-kenttään on syötetty jokin teksti.

[^1]: Tässä oletetaan, että käytetään oletusarvoin NetBeansin sulautettua web-palvelinta.

![ui-2](../img/w4e04-2.png "ui-2"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 2. Numeron lisäys.</small>

*Lisää numero* -sivulle päästään klikkaamalla *Hae numeroita* -sivulla olevaa ao. linkkiä tai tekemällä pyyntö suoraan esim. osoitteeseen `http://localhost:8383/W4E04/#!/bart/add` (Kuva 2). Sivulla on `Nimi`-kenttä on valmiiksi täytetty ao. henkilöllä, mutta kentän sisältöä voi muuttaa. Klikkaamalla `Lisää` -painiketta `Numero`-kenttään kirjattu puhelinnumero tallentuu henkilölle ja *Hae numeroita* -sivu palaa selaimen ikkunaan siten, että esillä on juuri *Lisää numero* -sivulla käsitellyn henkilön tiedot. `Peruuta` -painikkeen klikkaus tuo esiin *Hae numeroita* -sivun tallentamatta uutta numeroa muistioon.

![ui-3](../img/w4e04-3.png "ui-3"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 3. Numeron poisto.</small>

*Poistetaanko numero?* -sivulle päästään klikkaamalla *Hae numeroita* -sivulla olevaa ao. linkkiä tai tekemällä pyyntö suoraan esim. osoitteeseen `http://localhost:8383/W4E04/#!/bart/remove/222` (Kuva 3). Sivulla on `Nimi`-kenttä on valmiiksi täytetty ao. henkilöllä ja `Numero` -kenttässä on henkilöltä poistettava puhelinnumero. Kenttien sisältöä ei voi muuttaa. Klikkaamalla `Poista` -painiketta `Numero`-kenttään kirjattu puhelinnumero poistuu henkilöltä ja *Hae numeroita* -sivu palaa selaimen ikkunaan siten, että esillä on juuri *Poistetaanko numero?* -sivulla käsitellyn henkilön tiedot. `Peruuta` -painikkeen klikkaus tuo esiin *Hae numeroita* -sivun poistamatta numeroa muistiosta.


{% highlight html %}

    <body ng-app="PuhApp">

        <h1>Puhelinmuistio</h1>

        <div ng-view></div>

        <script src="js/PuhAppModule.js"></script>        
        <script src="js/PuhService.js"></script>
        <script src="js/wjr-btn.js"></script>

        <script src="todo/PuhController.js"></script>
        <script src="todo/AddController.js"></script>
        <script src="todo/RemoveController.js"></script>

        <script src="todo/config.js"></script>

    </body>

{% endhighlight %}

<small>Listaus 1.</small>

Sovelluksen `index`-tiedoston (*Listaus 1*) viittaamista tiedostoista `PuhAppModule.js` on valmiina sisältäen angular-moduulin luonnin sekä alustusdatan palvelua varten. Tiedostot `wjr-btn.js` ja `PuhService.js` voi kopioida sellaisenaan [Tehtävän 4.3](../tehtava43) ratkaisusta. Halutessaan voi injektoida henkilöitä ja numeroita sisältävän alustusdatan palveluun:

{% highlight js %}

PuhApp.service('PuhService', function (InitialData) {

    let henkilot = InitialData ? InitialData : {};

    ...
});

{% endhighlight %}

<small>Listaus 2.</small>


Pohjan runkoon laadittava `config.js` määrittelee sovelluksen reitityksen. Tiedostoissa `PuhController.js`, `AddController.js` ja `RemoveController.js` on konrollerien rungot kullekin sovelluksen näkymälle, joihin  liittyvät templatet (`search.html`, `add.html` ja `remove.html`) ovat pohjassa valmiina projektin `view`-kansiossa.


**Palauta** tehtävästä tiedostot `config.js`, `PuhController.js`, `AddController.js` ja `RemoveController.js`. Varmista ennen palautusta, että sovellus toimii odotetusti. Jos pohjakoodi sisältää testejä, varmista myös niiden läpimeno ilman virheilmoituksia.


### Lisätietoja

AngularJS:n reititystä käsitellään lyhyesti Web-selainohjelmointi-aineiston [luvussa 15][weso-15].

[weso-15]: http://web-selainohjelmointi.github.io/#15-Reititys-Angularissa

AngularJS:n versioon 1.6 on tullut pieni [reititykseen liittyvä muutos][stackoverflow]. Tämä ei kuitenkaan vaikuta mitenkään tehtävän ratkaisuun, koska se on huomioitu pohjassa olevassa templatessa.

[stackoverflow]: https://stackoverflow.com/questions/41185392/angularjs-1-6-routing-not-working/41852331>


<br/>

