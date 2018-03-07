---
layout: exercise_page
title: "Tehtävä 1.5 Puhelinmuistio - \"MVC\" (3p)"
exercise_template_name: W1E05.PuhMVC
exercise_discussion_id: 96768
exercise_upload_id: 378570
modified_at: 7.3.2018
---

Laadi puhelinmuistiosta MVC-sunnittelumallia mukaileva toteutus. Ratkaisu koostuu kolmesta `new`-operaattorilla kursuttavasta funktiosta, `Model`, `View` ja `Controller`, jotka laaditaan tehtäväpohjan `todo`-hakemistossa oleviin tiedostoihin, `model.js`, `view.js` ja `controller.js`.

*Malliin* (`Model`) tallennetaan puhelinmuistion data. *Näkymä* (`View`) rakentaa käyttöliittymän mallin datalle. *Kontrolleri* (`Controller`) vastaanottaa käyttöliitymästä mallin dataan liittyviä pyyntöjä. Sovelluksen alustuksen (`js/app.js`) jälkeen muistio toimii seuraavan kaavion mukaan:

![Oliokaavio](../img/mvc-kaavio.png "Oliokaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 600px;"}

<small>Kuva 1. Oliokaavio.</small>

*Kontrollerin* metodit (`haeNumerot`, `lisaaNumero`, `poistaNumero`) on kytketty html-dokumentissa olevien painonappien click-tapahtumien käsittelijöiksi. Ne kutsuvat *mallin* vastaavia metodeja (`annaNumerot`, `lisaaNumero`, `poistaNumero`) parametreilla, jotka on poimittu dokumentista  (`#nimi`, `#numero`) tai tapahtumaobjektista (`e`). *Malli* suorittaa metodikutsujen edellyttämät datan päivitysoperaatiot ja pyytää *näkymää* muodostamaan (`paivita`) tilannetta vastaavan käyttöliittymän. *Näkymä* rakentaa käyttöliittymän määrättyyn paikkaan (`#numerot`) html-dokumentissa.

Seuraavassa MVC-olioden rakenne on esitetty UML-luokkina:

![MVC-luokat](../img/mvc-luokat.png "MVC-luokat"){: style="display: block; margin: auto; margin-top: 10px; width: 650px;"}

<small>Kuva 2. MVC-luokat.</small>


Edellisten puhelinmuistio-tehtävävien tapaan  pohjakoodi sisältää puhelinmuistion  käyttöliittymän merkkauksen (vrt. [Tehtävä 1.1](../../osa1/tehtava11)). Tässä kuitenkin käyttöliittymää käsittelevä ja sieltä pyyntöjä vastaanottava koodi tulee jäsentää laadittaviin muodostinfunktioihin.

**Palauta** tehtävästä tiedostot `model.js`, `view.js` ja `controller.js`, jotka määrittelevät funktiot `Model`, `View` ja `Controller`. Varmista ennen palauttamista, että tehtäväpohjan sisältämät testit menevät läpi ilman virheilmoituksia.


### Vihjeitä ja lisätietoja

#### MVC-olioiden muodostaminen

Sovelluksen alustamisen suorittava koodi löytyy tehtävän pohjakoodista tiedostosta `js/app.js`:

{% highlight javascript %}

$(() => {
    // MVC-oliot
    const view = new View( $('#numerot') );
    const model = new Model(view);    
    const controller = new Controller(model, $('#nimi'), $('#numero'));
    // kontrollerin metodien sitominen painikkeisiin
    $('#etsi').click(controller.haeNumerot);
    $('#lisaa').click(controller.lisaaNumero);
    view.asetaPoistaja(controller.poistaNumero);
});

{% endhighlight %}

<small>Listaus 1.</small>

#### MVC-luokkien rungot

Seuraavassa on *Kuvan 2* luokkaesitystä vastaavat tehtävässä laadittavien muodostinfunktioiden rungot:

{% highlight javascript %}

function Model (view) {
    var henkilot = {};
    this.annaNumerot = function (nimi) {};
    this.lisaaNumero = function (nimi, numero) {};
    this.poistaNumero = function (nimi, numero) {};
};

{% endhighlight %}

<small>Listaus 2.</small>


{% highlight javascript %}

function View(jqNumerot) {
    var poistaNumero = function(){};
    this.asetaPoistaja = function (funktio) {
        poistaNumero = funktio;
    };    
    this.paivita = function (nimi, numerot) {};  
}

{% endhighlight %}

<small>Listaus 3.</small>


{% highlight javascript %}

function Controller(model, jqNimi, jqNumero) {
    this.haeNumerot = function () {};
    this.lisaaNumero = function () {};
    this.poistaNumero = function (e) {};
}

{% endhighlight %}

<small>Listaus 4.</small>


Tässä tehtävässä laadittava `Model` voi olla likimain sama kuin
[Tehtävän 1.4](../tehtava14) ratkaisuna oleva `Puhelinmuistio`-funktio. Tilanne poikkeaa tässä kuitenkin niin, että mallin metodit kutsuvat näkymän `paivita`-metodia. Funktioihin `View` ja `Controller` tulevan koodin voi muodostaa melko pitkälle aikaisempien tehtävien (1.1-1.4) pohjassa plevan tiedoston `js/app.js` koodin pohjalta.

#### Esimerkki

Tehtävän ratkaisu on periatteeltaan samankaltainen kuin oheismateriaalin [kohdassa 9.1](http://web-selainohjelmointi.github.io/#9.1-Esimerkki:-Muistuttaja) oleva Muistuttaja-esimerkki:

![Muistutus-olio](../img/muistutus_olio_21.png "Muistutus-olio"){: style="display: block; margin: auto; margin-top: 10px; width: 300px;"}

<small>Kuva 3. Muistutus-olio.</small>

Esimerkissä on tähän tehtävään verrattuna rakenteellisia tasoja enemmän. Kukin muodostinfunktio on paketoitu omaan olioonsa (`view`, `domain`, `controller`) ja muodostimille on annettu niiden tehtävää kuvaavat nimet. Tämä ratkaisu on luonteva erityisesti silloin, kun sovelluksessa on useita *malleja*, *näkymiä* ja/tai *kontrollereita*. 
