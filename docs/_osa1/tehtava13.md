---
layout: exercise_page
title: "Tehtävä 1.3 Puhelinmuistio - \"Capsule\" (3p)"
exercise_template_name: W1E03.PuhCapsule
exercise_discussion_id: 96766
exercise_upload_id: 378568
modified_at: 7.3.2018
---

Toteuta tehtäväpohjan `todo`-hakemiston tiedostoon `puhelinmuistio.js` koodi,
joka muodostaa olion `puhelinmuistio` siten, että puhelinmuistioon liittyvää dataa (nimiä ja numeroita) ei voi käsitellä olion metodien ulkopuolelta. UML-luokkana esitettynä olion rakenne on seuraavanlainen:

![Puhelinmuistio](../img/puhelinmuistio_moduuli.jpeg "Puhelinmuistio"){: style="display: block; margin: auto; margin-top: 10px; width: 300px;"}

<small>Kuva 1. Puhelinmuistio-luokka.</small>


Olioon laadittava `_reset`-metodi on tarkoitettu testausta varten. Se asettaa puhelinmuistion datan alkuarvoonsa (tyhjä olio). Oliokaaviona puhelinmuistio näyttää seuraavalta:

![Oliokaavio](../img/puhelinmuistio_sulkeuma.png "Oliokaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 600px;"}

<small>Kuva 2. Oliokaavio.</small>

Tehtäväpohjassa on laadittavaa oliota hyödyntävä valmis käyttöliittymä (vrt. [Tehtävä 1.1](../tehtava11)). Tässä tarvittava koodi on lähes sama kuin edellisissä tehtävissä - ainoastaan jäsennys on hieman toisenlainen.


**Palauta** tehtävästä `puhelinmuistio`-olion muodostava tiedosto `puhelinmuistio.js`. Varmista ennen palauttamista, että tehtäväpohjan sisältämät testit menevät läpi ilman virheilmoituksia.

### Vihjeitä ja lisätietoja

Oheismateriaalin [kohdassa 8.2](http://web-selainohjelmointi.github.io/#8.2-Moduulit) on tehtävään liittyvä esimerkki, jossa rakennetaa ostoskori-olion muodostava koodi. Olion rakenne esimerkissä on seuraavanlainen:


![Ostoskori-luokka](../img/ostoskori_moduuli.jpeg "Ostoskori-luokka"){: style="display: block; margin: auto; margin-top: 10px; width: 300px;"}

<small>Kuva 3. Ostoskori-luokka.</small>


Koodissa on ilman erillistä kutsua suoritettava anonyymifunktio, jonka paluuarvona on muodostettava olio. `ostokset` on funktion sisällä esitelty muuttuja, ja `lisaaOstos` ja `tuotteitaYhteensa` ovat funktion sisällä määriteltyjä toisia funktioita. `lisaa` ja `tuotteidenLukumaara` ovat funktion palauttaman olion metodeja.

Funktio on anonyymi, jos sille ei määrittelyn yhteydessä anneta nimeä:


{% highlight javascript %}

    function() {
      // ...
    }

{% endhighlight %}

<small>Listaus 1.</small>


Funktio suoritetaan määrittelyn yhteydessä ilman erillistä kutsua, jos se on asetettu sulkumerkkien sisään:


{% highlight javascript %}

    (function() {
      // ...
    })();

{% endhighlight %}

<small>Listaus 2.</small>


Ostoskorin koodi rakentuu esimerkissä seuraavasti:


{% highlight javascript %}

  var ostoskori = (function() {

    // sisäiset muuttujat

    var ostokset = [];

    // sisäiset funktiot

    function lisaaOstos(tuotteenNimi) {
      // ...
    }

    function tuotteitaYhteensa() {
      // ...
    }

    // rajapinta

    return {
        lisaa: lisaaOstos,
        tuotteidenLukumaara: tuotteitaYhteensa
    };

  })();

{% endhighlight %}

<small>Listaus 3.</small>


Edellä palautettavan olion metodit (`lisaa`, `tuotteidenLukumaara`) ovat viitteitä funktion sisäisiin funktioihin (`lisaaOstos`, `tuotteitaYhteensa`), jotka käsittelevät funktion sisällä esiteltyä muuttujaa `ostokset`. Metodien ja metodien viittaamien sisäfunktioden nimet voivat olla samoja (, mikä lienee usein luontevaa):


{% highlight javascript %}

  var ostoskori = (function() {

    // ...  

    function lisaa(tuotteenNimi) {
      // ...
    }

    function tuotteidenLukumaara() {
      // ...
    }

    return {
        lisaa: lisaa,
        tuotteidenLukumaara: tuotteidenLukumaara
    };

  })();

{% endhighlight %}

<small>Listaus 4.</small>


Palautettavan olion metodit voidaan myös määritelä anonyymifunktiona palautettavan olion määrittelyn osana:


{% highlight javascript %}

  var ostoskori = (function() {

    var ostokset = [];

    return {
        lisaa: function(){
          // ...
        },
        tuotteidenLukumaara: function(){
          // ...
        }
    };

  })();

{% endhighlight %}

<small>Listaus 5.</small>


Edellä olevan koodin suorituksen jälkeinen tilanne voidaan esittää oliokaaviona  seuraavasti:


![Oliokaavio](../img/ostoskori_sulkeuma.png "Oliokaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 600px;"}

<small>Kuva 4. Ostoskori-oliokaavio.</small>
