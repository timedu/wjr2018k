---
layout: exercise_page
title: "Tehtävä 4.3: Puhelinmuistio: Directive (3p)"
exercise_template_name: W4E03.PuhDirective
exercise_discussion_id: 99282
exercise_upload_id: 382323
modified_at: 18.4.2018
---


Jatkokehitä *AngularJS*-pohjaista puhelinmuistio-sovellustasi siten, että painikkeiden omainaisuudet määrittelee erillinen *direktiivi*. Sovelluksen ulkoasu ja ulkoinen käyttäytyminen pysyy muuttumattomana.

Tehtävissä [4.1](../tehtava41) ja [4.2](../tehtava42) näkymän (`template.html`) merkkaus on seuraavanlainen:

{% highlight html %}
{% raw %}

<div ng-controller="PuhController">

    <div id="lomake">
        ...
        <button id="lisaa" ng-click="add()">Lisää</button>
    </div>

    <div id="luettelo">                
        ...
            <li ng-repeat="numero in numerot">
                {{numero}}
                <button ng-click="remove(nimi, numero)">X</button>
            </li>
        </ul>                
    </div>

</div>


{% endraw %}
{% endhighlight %}


Merkkaus sisältää kaksi painiketta (`button`). Molemmille painikkeille on `ng-click`-direktiivillä määritelty tapahtumakäsittelijä. `button`-elementtien sisältönä oleva teksti näkyy sivulla painikkeiden otsikkona.

Tämän tehtävän pohjakoodissa vastaava tiedosto on seuraavanlainen:

{% highlight html %}
{% raw %}

<div ng-controller="PuhController">

    <div id="lomake">
        ...
        <button wjr-btn="add"></button>
    </div>

    <div id="luettelo">
        ...             
            <li ng-repeat="numero in numerot">
                {{numero}}
                <button wjr-btn="remove" 
                        otsikko="X"
                        nimi="{{nimi}}" 
                        numero="{{numero}}">                            
                </button>
            </li>
        </ul>                
    </div>
        
</div>

{% endraw %}
{% endhighlight %}

Painikkeilla ei ole `ng-click`-direktiiviä eikä sisältöä. Näiden sijaan painikkeilla on tässä tehtävässä määriteltävä `wjr-btn`-direktiivi. Poisto-painikkeella on myös attribuutit `otsikko`, `nimi` ja `numero`, joista kahden viimeisen arvona on numeron poistossa tarvittavat tiedot. Direktiivi laaditaan pohjassa olevaan runkoon, `wjr-btn.js`:

{% highlight javascript %}

PuhApp.directive('wjrBtn', function () {

});

{% endhighlight %}

Direktiivi otsikoi painonapin sekä asettaa sille `click`-tapahtuman käsittelijän.

Painikkeiden otsikon määrittelee elementin `otsikko`-attribuutin arvo. Jos otsikkotekstiä ei ole näin määritelty, otsikoksi asetetaan  `wjr-btn`-attribuutin arvo.

Painikkeen `click`-tapahtuman käsittelijäksi asetetaan funktio, joka kutsuu ao. kontrollerin määrittelemää metodia. Jos `wjr-btn`-attribuutin arvona on `add`, tapahtumakäsittelijä kutsuu metodia `add` so. attribuutin arvo määrää kutsuttavan metodin. Metodikutsun parametriksi annetaan objekti, joka sisältää kaikki elementin sisältämät attribuutit.

Sovelluksen pohjassa olevan pääsivun `index.html` merkkaus on seuraava:

{% highlight html %}

    <body ng-app="PuhApp">

        <h1>Puhelinmuistio</h1>

        <div ng-include=" 'view/template.html'"></div>

        <script src="js/PuhAppModule.js"></script>
        <script src="js/PuhService.js"></script>
        <script src="js/PuhController.js"></script>
        
        <script src="todo/wjr-btn.js"></script>

    </body>

{% endhighlight %}

Pääsivun viittaamista tiedostoista `template.html` ja `PuhAppModule.js` ovat pohjassa valmiina. Tiedostot `PuhService.js` ja `PuhController.js`[^1] voi kopioida edellisen tehtävän ratkaisusta. *Direktiivi* laaditaan tiedostoon `wjr-btn.js`. 

[^1]: Kontrollerin `remove`-metodin otsikon on kuitenkin oltava muotoa `function({nimi, numero})`, jolloin metodikutsun välittämästä objektista saadaan tarvittavat tiedot muuttujiin `nimi` ja `numero` ([destructuring assignment][destructuring_assignment]).

[destructuring_assignment]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

**Palauta** tehtävästä tiedosto `wjr-btn.js`. Varmista ennen palautusta, että sovellus toimii odotetusti. Jos pohjakoodi sisältää testejä, varmista myös niiden läpimeno ilman virheilmoituksia.

### Lisätietoja

AngularJS -direktiivejä käsitellään lyhyesti Web-selainohjelmointi -aineiston [kohdassa 12.6][weso-12.6]. Laajempi esitys asiasta löytyy AngularJS:n [kehittäjän oppaasta][guide].

[weso-12.6]: http://web-selainohjelmointi.github.io/#12.6-Direktiivit
[guide]: https://docs.angularjs.org/guide/directive

*AngularJS*:n elementti-objektit muistuttavat hieman *jQuery*-objekteja, mutta esim. läheskään kaikki *jQuery*:n metodit eivät ole käytettävissä, ks. [angular.element][angular.element].

[angular.element]: https://docs.angularjs.org/api/ng/function/angular.element


<br/>

