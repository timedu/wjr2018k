---
layout: exercise_page
title: "Tehtävä 3.2: Elokuvat"
exercise_template_name: W3E02.Elokuvat
exercise_discussion_id: 98572
exercise_upload_id: 381426
modified_at: 3.4.2018
---

Laadi tehtäväpohjaan template siten, että se listaa osana dokumentia
`MovieController` -kontrollerissa[^2] määritellyn taulukon[^3]  elokuvat siten,
että lista vastaa pohjassa olevaa  vakiomerkkausta[^1].

[^1]: Merkkaus on tiedostossa `index.html`.
[^2]: `MovieController` on määritelty tiedostossa `js\controller.js`.
[^3]: `$scope.movies`

Elokuvan otsikko sisältää sen nimen ja julkaisuvuoden.
Elokuvan nimen tulee olla linkki sen sivulle [IMDb](http://www.imdb.com/):ssä.
Oscar-palkinnot tulee näyttää vain, jos elokuvalla niitä on.
"Oscar awards" otsikon vieressä suluissa on Oscar-palkintojen lukumäärä.
Elokuvan näyttelijät tulee listata niin, että näyttelijän nimi on ensin ja
sen jälkeen suluissa näyttelijän roolinimi elokuvassa.
Järjestä elokuvien lista julkaisuvuoden perusteella
niin, että uusin elokuva on listan kärjessä.

**Palauta** tehtävästä tiedosto `template.html`, jonka runko löytyy `todo`-hakemistosta. Varmista, että tehtäväpohjassa olevat testit menevät läpi ennen palautusta.

### Lisätietoja

Tämä tehtävä on lähes sama kuin lähteen
[Tehtävä 28](http://web-selainohjelmointi.github.io/#vk-4-t28),
jonka edellä materiaalissa käsitellään tehtävän ratkaisua tukevia asioita.

Direktiivit
[ng-repeat](https://docs.angularjs.org/api/ng/directive/ngRepeat),
[ng-href](https://docs.angularjs.org/api/ng/directive/ngHref),
[ng-if](https://docs.angularjs.org/api/ng/directive/ngIf) ja
[ng-repeat](https://docs.angularjs.org/api/ng/directive/ngRepeat)
lienevät tässä tarpeellisia. Myös filtteriä
[orderBy](https://docs.angularjs.org/api/ng/filter/orderBy)
varmaankin tarvitaan.

<br/>
