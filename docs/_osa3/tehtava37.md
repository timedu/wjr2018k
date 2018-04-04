---
layout: exercise_page
title: "Tehtävä 3.7: Muistilista (4p)"
exercise_template_name: W3E07.Muistilista
exercise_discussion_id: 98577
exercise_upload_id: 381431
modified_at: 4.4.2018
---


Toteuta edellisiä tehtäviä hieman laajempi sovellus, *muistilista*, jonka avulla käyttäjä voi lisätä, priorisoida ja poistaa tehtäviä sekä merkata niitä tehdyksi. Sovellus esittää muistilistan tehtävät niiden prioriteetin mukaisessa järjestyksessä. Muistilistan ulkoasu on seuraavanlainen:

![Muistilista](../img/muistilista.png "Muistilista"){: style="display: block; margin: auto; margin-top: 10px; width: 600px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}


Toteuta sovellukseen seuraavat toiminnot:

* Käyttäjä voi lisätä tehtävän listaan "Uusi tehtävä"-tekstikentän nimen perusteella. Älä anna käyttäjän lisätä tehtävää tyhjällä nimellä.
* Käyttäjä voi merkata merkata tehtävän tehdyksi klikkaamalla checkboxia. Tehdyn tehtävän nimi vedetään yli (voit lisätä tehtävän nimeen tällöin luokan `todo-done` ([ng-class][ng-class]).
* Käyttäjä voi merkata kaikki tehtävät tehdyksi klikkaamalla "Merkkaa kaikki tehdyiksi" -painiketta.
* Käyttäjä voi poistaa tehtävän listasta painamalla oikeasta laidasta "Poista"-painiketta.
* Käyttäjä voi poistaa kaikki tehtävät klikkaamalla "Poista kaikki"-painiketta. Varmista painikkeen klikkaamisen jälkeen, että käyttäjä haluaa varmasti poistaa kaikki tehtävät ([confirm][confirm]).
* Tehtävään liittyy prioriteetti. Jokaiselle tehtävälle lisätään sen lisäämisen yhteydessä prioriteetti 1. Mitä pienempi prioriteetti on, sitä tärkeämpi tehtävä on. Käyttäjä voi muokata tehtävän prioriteettia vaihtamalla sen vieressä olevan tekstikentän arvoa. Järjestä tehtävät prioriteetin mukaan niin, että tärkeimmät tehtävät ovat listan yläpäässä. Liitä prioriteetin sisältävään tekstikenttään [ng-blur][ng-blur] -kuuntelija ja siihen liittyvä funktio, joka tekee prioriteetin muutoksen. Lajittelun voi toteuttaa [orderBy][orderBy]-filtterin avulla.
* Käyttäjä voi nähdä muistilistan alalaidasta, kuinka monta tehtävää hän on tehnyt ja kuinka monta on vielä tekemättä. Käytä selkeää suomen kieltä, jolloin `1 tehtävä tehty` on oikein ja `1 tehtävää tehty` on väärin (vihje: [ng-pluralize][ng-pluralize]). Toteuttaa toiminto käyttämällä [$watch][watch] -funktiota niin, että seuraat tehtävät sisältävää taulukkoa ja päivität  muuttujien `todosDone` ja `todosRemaining` arvot aina, kun taulukossa tapahtuu muutoksia. Muista lisätä `$watch` -funktiokutsun viimeiseksi parametriksi `true`, niin Angular tarkastaa onko taulukossa tapahtunut muutoksia sen sisällön, eikä pelkän viitteen perusteella.

[ng-class]: https://docs.angularjs.org/api/ng/directive/ngClass
[confirm]: https://developer.mozilla.org/en-US/docs/Web/API/Window/confirm
[ng-blur]: https://docs.angularjs.org/api/ng/directive/ngBlur
[ng-pluralize]: https://docs.angularjs.org/api/ng/directive/ngPluralize
[watch]: https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$watch
[orderBy]: https://docs.angularjs.org/api/ng/filter/orderBy

Käytä seuraavia näkyvyysalueen tunnisteita, joihin myös pohjan testit perustavat toimintansa:

~~~
+-----------------------------+   +-----------------------------+
| TodoController ($scope)     |   | Todo                        |
+-----------------------------+   +-----------------------------+
| todos: Array of Todo        |   | task: String                |
| todosDone: Number           |   | priority: Number            |
| todosRemaining: Number      |   | done: Boolean               |
| newTask: String             |   +-----------------------------+
+-----------------------------+
| add()                       |
| remove(todo)                |
| removeAll()                 |
| toggleDone(todo)            |
| changePriority(todo, event) |
| setAllDone()                |
+-----------------------------+
~~~

**Palauta** tehtävästä tiedostot `TodoTemplate.html` ja `TodoController.js`, joiden rungot löytyvät `todo`-hakemistosta. Varmista, että tehtäväpohjassa olevat testit menevät läpi ennen palautusta. Sovelluksen muut rakenne-osat ovat tehtäväpohjassa valmiina.

### Lisätietoja

Tehtävä on lähes sama kuin lähteen [Tehtävä 33][tehtäva-33]. Tehtävässä on sovellettava suhteellisen paljon materiaalin [luvun 12][luku-12] käsittelemistä asioista.

[tehtäva-33]: http://web-selainohjelmointi.github.io/#vk-4-t33
[luku-12]: http://web-selainohjelmointi.github.io/#12-Sovelluksen-rakenteen-hallinta:-AngularJS
