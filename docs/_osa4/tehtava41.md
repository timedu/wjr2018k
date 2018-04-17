---
layout: exercise_page
title: "Tehtävä 4.1: Puhelinmuistio: AngularJS"
exercise_template_name: # W4E01.PuhAngular
exercise_discussion_id: # 99280
exercise_upload_id: # 382321
modified_at: 16.4.2018
kesken: 1
julkaisu: 18.4.2018
no_review: 1
---

Puhelinmuistio: AngularJS

{% comment %}

Laadi [osan 1](../../osa1) tehtävistä tuttu puhelinmuistio-sovellus[^0] nyt kuitenkin AngularJS -toteutuksena.

[^0]: Tässä ei aiemmista versioista poiketen ei ole mukana Bootstrap-tyylejä.


Seuraavassa on projektipohjassa oleva sovelluksen pääsivu:

{% highlight html %}

    <body ng-app="PuhApp">
        <h1>Puhelinmuistio</h1>

        <div ng-include=" 'view/template.html'"></div>

        <script src="js/PuhAppModule.js"></script>
        <script src="js/puhelinmuistio.js"></script>

        <script src="todo/controller.js"></script>
    </body>

{% endhighlight %}

Pääsivun viittaamista  tiedostoista kolme (`template.html` `AppModule.js` ja `puhelinmuistio.js`) on pohjassa valmiina. `template.html` muodostaa puhelinmuistion käyttöliittymän ja tiedostossa `puhelinmuistio.js`[^1] oleva koodi ylläpitää tietoja muistioon talletetuista nimistä ja numeroista. Tehtävänä on täydentää tiedostoa `controller.js` niin, että käyttöliittymä esittää muistioon talletettuja numeroita ja, että käyttöliittymän kautta voi ylläpitää  muistion tietoja so. lisätä ja poistaa nimeen liittyviä numeroita. `PuhAppModule.js` määrittelee moduulin, joka sisältää täydennettävän kontrollerin.

[^1]: Kopioitu lähes sellaisenaan  erään aiemman tehtävän ratkaisuluonnoksesta.

Seuraavassa on sovelluksen käyttöliittymä:



![UI](../img/w4e01ui.png "UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 1. </small>


`Nimi`-kenttään kirjatulle henkilölle lisätään `Puhelinnumero` -kenttään kirjattu numero klikattaessa `Lisää`-painiketta. Numero poistuu henkilöltä klikataessa `X`-painiketta. Muutokset näkyvät klikkausten myötä heti myös käyttöliittymässä.

[Aiempien tehtävien](../../osa1) puhelinmuistio -toteutuksista poiketen tässä ei ole *Etsi* -painiketta. Henkilölle talletetut numerot ilmestyvät sivulle heti, kun `Nimi`-kenttään[^2] on kirjattu henkilö, jolle on talletettu numeroita.

[^2]: numerot tulevat esiin, vaikka kursori olisi edelleen `Nimi`-kenttässä


Puhelinmuistio näkyy objektissa `puh`, jota käsitellään metodeilla `anneNumerot`, `lisaaNumero` ja `poistaNumero` (ks. `puhelinmuistio.js`) 

**Palauta** tehtävästä tiedosto `controller.js`. Varmista ennen palautusta, että sovellus toimii odotetusti. Varmista myös testien läpimeno ilman virheilmoituksia.


<br/>

{% endcomment %}
