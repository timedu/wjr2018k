---
layout: exercise_page
title: "Tehtävä 4.2: Puhelinmuistio: Service"
exercise_template_name: # W4E02.PuhService
exercise_discussion_id: # 99281
exercise_upload_id: # 382322
modified_at: 16.4.2018
kesken: 1
julkaisu: 18.4.2018
no_review: 1
---

Puhelinmuistio: Service

{% comment %}

Laadi [edellisen tehtävän](../tehtava41) kaltainen *AngularJS*-pohjainen toteutus puhelinmuistioista kuitenkin niin, että nimi- ja numerotietojen ylläpidon toteuttaa erillinen *Muistio*-palvelu.

Seuraavassa on projektipohjassa oleva sovelluksen pääsivu, joka ei juuri poikkea edellisen tehtävän vastaavasta:

{% highlight html %}

    <body ng-app="PuhApp">
        <h1>Puhelinmuistio</h1>

        <div ng-include=" 'view/template.html' "></div>

        <script>var PuhApp = angular.module('PuhApp', []);</script>

        <script src="todo/controller.js"></script>
        <script src="todo/service.js"></script>

    </body>

{% endhighlight %}

Merkkauksen viittaama pohjassa valmiina oleva `template.html` on täysin sama kuin *Tehtävässä 5.1*. `controller.js` edellyttää pieniä muutoksia: siihen on injektoitava *Muistio*-palvelu ja numerotietojen ylläpidossa on tukeuduttava tähän palveluun.

`Muistio`-palvelu laaditaan pohjassa olevaan runkoon, `service.js`:

{% highlight javascript %}

PuhApp.service('Muistio', function () {

    // ...

});

{% endhighlight %}

Palvelu toimii tässä aivan samoin kuin Tehtävässä 5.1 käytetty `muistio.Model`-funktiolla luotu olio. Palvelun rakennetta voidaan kuvata seuraavanlaisella UML-luokalla:

~~~
    +-----------------------+
    |        Muistio        |
    |-----------------------|
    | -henkilot = {}        |
    |-----------------------|
    | +annaNumerot(): Array |
    | +lisaaNumero()        |
    | +poistaNumero()       |
    +-----------------------+
~~~


**Palauta** tehtävästä tiedostot `controller.js` ja `service.js`. Varmista ennen palautusta, että sovellus toimii odotetusti. Jos pohjakoodi sisältää testejä, varmista myös niiden läpimeno ilman virheilmoituksia.

### Lisätietoja


AngularJS -palveluja käsitellään lyhyesti kurssilukemiston [kohdassa 13.2][weso-13.2]. Laajempi esitys asiasta löytyy AngularJS:n [kehittäjän oppaasta][guide].

[weso-13.2]: {{site.baseurl}}/weso/#13.2-Palvelut-(services)
[guide]: https://docs.angularjs.org/guide/services

{% endcomment %}
