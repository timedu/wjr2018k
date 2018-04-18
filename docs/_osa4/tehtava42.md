---
layout: exercise_page
title: "Tehtävä 4.2: Puhelinmuistio: Service (2p)"
exercise_template_name: W4E02.PuhService
exercise_discussion_id: 99281
exercise_upload_id: 382322
modified_at: 18.4.2018
---


Laadi [edellisen tehtävän](../tehtava41) kaltainen *AngularJS*-pohjainen toteutus puhelinmuistioista kuitenkin niin, että nimi- ja numerotietojen ylläpidon toteuttaa erillinen palvelu, *PuhService*.

Seuraavassa on projektipohjassa oleva sovelluksen pääsivu, joka ei juuri poikkea edellisen tehtävän vastaavasta:

{% highlight html %}

    <body ng-app="PuhApp">
        <h1>Puhelinmuistio</h1>

        <div ng-include=" 'view/template.html'"></div>        
        <script src="js/PuhAppModule.js"></script>

        <script src="todo/PuhController.js"></script>
        <script src="todo/PuhService.js"></script>
    </body>

{% endhighlight %}

Merkkauksen viittaama pohjassa valmiina olevat `PuhAppModule.js` ja `template.html` ovat täysin samoja kuin [Tehtävässä 4.1](../tehtava41). `PuhController.js` edellyttää pieniä muutoksia: siihen on injektoitava *PuhService*-palvelu ja numerotietojen ylläpidossa on tukeuduttava tähän palveluun.

`PuhService`-palvelu laaditaan pohjassa olevaan runkoon, `PuhService.js`:

{% highlight javascript %}

PuhApp.service('PuhService', function () {

    // ...

});

{% endhighlight %}

Palvelu toimii tässä aivan samoin kuin Tehtävässä 4.1 käytetty `puh`-objekti. Palvelun rakennetta voidaan kuvata seuraavanlaisella UML-luokalla:

~~~
    +-----------------------+
    |       PuhService      |
    |-----------------------|
    | -henkilot = {}        |
    |-----------------------|
    | +annaNumerot(): Array |
    | +lisaaNumero()        |
    | +poistaNumero()       |
    +-----------------------+
~~~


**Palauta** tehtävästä tiedostot `PuhController.js` ja `PuhService.js`. Varmista ennen palautusta, että sovellus toimii odotetusti. Jos pohjakoodi sisältää testejä, varmista myös niiden läpimeno ilman virheilmoituksia.

### Lisätietoja


AngularJS -palveluja käsitellään lyhyesti Web-selainohjelmointi-aineiston [kohdassa 13.2][weso-13.2]. Laajempi esitys asiasta löytyy AngularJS:n [kehittäjän oppaasta][guide].

[weso-13.2]: http://web-selainohjelmointi.github.io/#13.2-Palvelut-(services)
[guide]: https://docs.angularjs.org/guide/services

