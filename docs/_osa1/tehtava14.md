---
layout: exercise_page
title: "Tehtävä 1.4 Puhelinmuistio - \"Cap Ctor\" (3p)"
exercise_template_name: W1E04.PuhCapCtor
exercise_discussion_id: 96767
exercise_upload_id: 378569
modified_at: 7.3.2018
---

[Tehtävässä 1.1](../tehtava11)
laadittiin funktio, joka luo new -operaattorin tuella puhelinmuistio-olioita. Muodostuvien olioiden ongelmaksi jäi se, että niiden sisältämää dataa ei kapseloitu so. dataan pääsi käsiksi metodien ulkopuolelta. [Tehtävässä 1.3](../tehtava13) ratkaisiin kapselointiin liittyvä ongelma, mutta esitetyllä tavalla voidaan tuottaa ainoastaa yksi olio.  

Tässä tehtävässä pohjan tiedostoon `todo/puhelinmuistio.js` laaditaan funktio `Puhelinmuistio`, jolla voidaan tuottaa useita olioita siten, että niiden dataa ei voi käsitellä metodien ulkopuolellta. Funktiota kutsutaan `new` -operaattorilla.


{% highlight javascript %}

var puhelinmuistio = new Puhelinmuistio();

{% endhighlight %}

<small>Listaus 1.</small>

Muodostuvien olioiden rakennetta voidaan kuvata seuraavalla luokkaesityksellä:

![Puhelinmuistio](../img/puhelinmuistio_luokka_13.png "Puhelinmuistio"){: style="display: block; margin: auto; margin-top: 10px; width: 300px;"}

<small>Kuva 1. Puhelinmuistio-luokka.</small>

Muodostin-funktion kutsun jälkeistä tilannetta voidaan kuvata seuraavalla oliokaaviolla:

![Oliokaavio](../img/puhelinmuistio_olio_13a.png "Oliokaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 600px;"}

<small>Kuva 2. Oliokaavio.</small>

Tehtäväpohjassa on laadittavaa oliota käyttävä valmis käyttöliittymä (vrt. [Tehtävä 1.1](../tehtava11)).

**Palauta** tehtävästä tiedosto `puhelinmuistio.js`, joka määrittelee funktion `Puhelinmuistio`. Varmista ennen palauttamista, että tehtäväpohjan sisältämät testit menevät läpi ilman virheilmoituksia.

### Vihjeitä ja lisätietoja

#### Ratkaisuperiaate

Tässä laadittavaa funktiota käytetään kuten [Tehtävässä 1.1](../tehtava11) laadittavaa muodostinta. Ratkaisut poikkeavat kuitenkin niin, että tässä data on muodostimen paikallinen muuttuja:

{% highlight javascript %}

function OlionMuodostin() {

  var data = {};

  this.metodi = function() {
    // käsittele dataa
  };

  // ei return-lausetta
}

// ...

var olio = new OlionMuodostin();

// ...

olio.metodi();

{% endhighlight %}

<small>Listaus 2.</small>

Tarvittava koodi on likimain sama kuin edellisissä tehtävissä - ainoastaan jäsennys on hieman toisenlainen.

#### Esimerkki

Oheismateriaalin [kohdassa 8.3](http://web-selainohjelmointi.github.io/#8.3-Olioiden-tila-ja-new) on tehtävään liittyviä esimerkkejä, joissa määritellään hivenen toisistaan poikkeavia  `Laskuri` -funktioita.
