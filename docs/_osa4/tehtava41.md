---
layout: exercise_page
title: "Tehtävä 4.1: Puhelinmuistio: Angular"
exercise_template_name: # W4E01.PuhAngular
exercise_discussion_id: #
exercise_upload_id: #
kesken:  1
no_review: 1
---


Laadi aikaisemmista tehtävistä tuttu puhelinmuistio-sovellus nyt kuitenkin AngularJS -toteutuksena.

Seuraavassa on projektipohjassa oleva sovelluksen pääsivu:

{% highlight html %}

    <body ng-app="PuhApp">
        <h1>Puhelinmuistio</h1>

        <div ng-include=" 'view/template.html' "></div>

        <script>var PuhApp = angular.module('PuhApp', []);</script>

        <script src="todo/controller.js"></script>
        <script src="js/model.js"></script>

    </body>

{% endhighlight %}

Pääsivun viittaamasta kolmesta tiedostoista kaksi (`template.html` ja `model.js`) on pohjassa valmiina. `template.html` muodostaa puhelinmuistion käyttöliittymän ja tiedostossa `model.js`[^1] oleva koodi ylläpitää tietoja muistioon talletetuista nimistä ja numeroista. Tehtävänä on täydentää tiedostoa `controller.js` niin, että käyttöliittymä esittää muistioon talletettuja numeroita ja, että käyttöliittymän kautta voi ylläpitää  muistion tietoja so. lisätä ja poistaa nimeen liittyviä numeroita.

[^1]: kopioitu suoraan aiemman tehtävän ratkaisuluonnoksesta

Seuraavassa on sovelluksen käyttöliittymä:

![ui](../img/w5e01ui.png "ui")

`Nimi`-kenttään kirjatulle henkilölle lisätään `Puhelinnumero` -kenttään kirjattu numero klikattaessa `Lisää`-painiketta. Numero poistuu henkilöltä klikataessa `X`-painiketta. Muutokset näkyvät klikkausten myötä heti myös käyttöliittymässä.

Aiempien tehtävien puhelinmuistio -toteutuksista poiketen tässä ei ole *Etsi* -painiketta. Henkilölle talletetut numerot ilmestyvät sivulle heti, kun `Nimi`-kenttään[^2] on kirjattu henkilö, jolle on talletettu numeroita.

[^2]: numerot tulevat esiin, vaikka kursori olisi edelleen `Nimi`-kenttässä

**Palauta** tehtävästä tiedosto `controller.js`. Varmista ennen palautusta, että sovellus toimii odotetusti. Jos pohjakoodi sisältää testejä, varmista myös niiden läpimeno ilman virheilmoituksia.


#### Alaviitteet
