---
layout: exercise_page
title: "Tehtävä 1.1 Puhelinmuistio - \"Prototype\" (3p)"
exercise_template_name: W1E01.PuhPrototype
exercise_discussion_id: 96764
exercise_upload_id: 378566
modified_at: 7.3.2018
---

Toteuta tehtäväpohjan `todo`-kansiossa olevaan tiedostoon `puhelinmuistio.js` funktio `Puhelinmuistio`, joka
[new](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)
-operattorilla kutsuttaessa luo puhelinmuistio-olioita. Muistioon voi lisätä ja sieltä voidaan poistaa nimiä ja numeroita. Jokaiseen nimeen voi liittyä useampi numero. Jos samalle henkilölle yritetään asettaa sama numero useampaan kertaan, numero tallennetaan henkilölle vain kerran. Useammalla henkilöllä voi olla sama numero. Funktiolla luotavien olioiden rakenne voidaan esittää seuraavanlaisena UML-luokkana [^1]:

[^1]: JavaScript ei sisällä luokkia, mutta tässä funktiolla luotavien olioiden rakenne noudattaa esitetyn luokan rakennetta.


![Puhelinmuistio](../img/puhelinmuistio_object.jpeg "Puhelinmuistio"){: style="display: block; margin: auto; margin-top: 10px; width: 350px;"}

<small>Kuva 1. Puhelinmuistio-luokka.</small>

Metodien lisäksi puhelinmuistio-oliolla on tietojen tallettamista varten attribuutti `_henkilot`[^2] . Attribuutti toteutetaan oliona, jossa kutakin muistioon talletettua henkilöä vastaa taulukko-tyyppinen attribuutti henkilön numeroiden tallettamista varten. Esimerkiksi seuraavassa kuvassa `_henkilot` -oliolla on kaksi taulukko-tyyppistä attribuuttia, `Flanders` ja `Bart Simpson`, joista ensimmäinen esiintyy jäljempänä esitettyssä käyttöliittymässä.   

[^2]: Attribuutin ensimmäisenä merkkinä oleva `_` indikoi tässä sitä, että attribuuttiin ei ole tarkoitus viitata olion metodien ulkopuolelta, vaikka se tässä toteutuksessa on mahdollista.

![Henkilot](../img/henkilot.jpeg "Henkilot"){: style="display: block; margin: auto; margin-top: 10px; width: 350px;"}

<small>Kuva 2. Henkilöt-objekti.</small>

Tässä laadittavalla funktiolla luodaan puhelinmuistio-olioita seuraavasti:

{% highlight javascript %}

var puhelinmuistio = new Puhelinmuistio();

{% endhighlight %}

Oliokaaviona syntynyt tilanne näyttää seuraavanlaiselta:

![Oliokaavio](../img/puhelinmuistio_rakenne.png "Oliokaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 700px;"}

<small>Kuva 3. Oliokaavio.</small>


**Palauta** tehtävästä `Puhelinmuistio`-funktion sisältävä tiedosto `puhelinmuistio.js`. Varmista ennen palauttamista, että tehtäväpohjan sisältämät [testit](../testit11/) menevät läpi ilman virheilmoituksia.

### Vihjeitä ja lisätietoja

#### Tehtäväpohjan käyttöliittymä

[Tehtäväpohjassa](../tehtavapohjasta) on tässä laadittavaa funktiota käyttävä valmis käyttöliittymä:

![Käyttöliittymä](../img/puhelinmuistio_ui.png "Käyttöliittymä"){: style="display: block; margin: auto; margin-top: 10px; width: 500px;"}

<small>Kuva 4. Käyttöliittymä.</small>

*Numeroiden lisääminen* muistioon tapahtuu kirjaamalla tiedot *Nimi*- ja *Numero*- syötekenttiin ja klikkaamalla *Lisää* -painonappia, minkä jälkeen numero tallentuu muistioon ja kaikki ko. nimeen liittyvät numerot ilmestyvät sivulle. *Numeroiden haku* suoritetaan kirjaamalla hakuehtona toimiva henkilön nimi sivun *Nimi* -kenttään ja klikkaamalla *Etsi*-painonappia. Tämän jälkeen nimeen liittyvät numerot ilmestyvät sivulle samoin kuin numeroita lisättäessä. Kunkin sivulla olevan numeron ohessa on *x* -painike, jota klikkaamalla *numero poistuu* sekä sivulta että muistiosta.

#### Esimerkki

Oheismateriaalin [kohdassa 8.1](http://web-selainohjelmointi.github.io/#8.1-Oliot) on tehtävään liittyvä esimerkki, jossa rakennetaa kirja-olioita muodostava `Kirja`-funktio. Olioiden rakenne esimerkissä on seuraavanlainen:

![Kirja-luokka](../img/kirja_olio.jpeg "Kirja-luokka"){: style="display: block; margin: auto; margin-top: 10px; width: 350px;"}

<small>Kuva 5. Kirja-luokka.</small>

JavaScriptissä ei ole olioden luokkia, mutta oliolla on tiedossa, sen luonut funktio. Jos esimerkin `Kirja`-funktiolla on luotu `kirja`-olio, tilannetta voidaan kuvata seuraavanlaisella oliokaaviolla:

![Oliokaavio](../img/kirja_rakenne.jpeg "Oliokaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 700px;"}

<small>Kuva 6. Kirja oliokaaviona.</small>


#### Viitteitä käsikirjaan

Tehtävän ratkaisussa esim. seuraavat apuveuvot saattavat olla hyödyllisiä:
[Array.prototype.includes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes),
[Array.prototype.indexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf),
[Array.prototype.push](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push),
[Array.prototype.slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice),
[Array.prototype.splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice),
[Object.keys](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys),
[delete operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete).

<br/>

Alaviitteet
