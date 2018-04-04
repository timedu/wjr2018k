---
layout: exercise_page
title: "Tehtävä 3.3: Elokuvahaku (1p)"
exercise_template_name: W3E03.ElokuvaHaku
exercise_discussion_id: 98573
exercise_upload_id: 381427
modified_at: 3.4.2018
---

Muokkaa tehtäväpohjan tiedostoa `template.html` siten, että sen muodostamaa elokuvien listaa pystyy filtteröimään nimen, julkaisuvuoden ja ohjaajan perusteella käyttämällä sivulla olevia kenttiä. Jos siis käyttäjä syöttää esimerkiksi "*nimi*"-kenttään arvon "*The Lord*" ja "*ohjaaja*"-kenttään arvon "*Peter*", tulee dokumentin esittää vain elokuvat, joiden nimestä löytyy sana "*The Lord*" ja ohjaajan nimestä löytyy sana "*Peter*".

**Palauta** tehtävästä tiedosto `template.html`, jonka runko löytyy `todo`-hakemistosta. Varmista, että tehtäväpohjassa olevat testit menevät läpi ennen palautusta.  


### Lisätietoja

Tämä on tehtävä on lähes sama kuin lähteen
[Tehtävä 29](http://web-selainohjelmointi.github.io/#vk-4-t29), jonka edellä materiaalissa käsitellään tehtävän ratkaisua tukevia asioita.

Filttereistä löytyy tietoja *AngularJS* -käsikirjan [ao. sivulta](https://docs.angularjs.org/api/ng/filter/filter).

Elokuvataulukko (`$scope.movies`) löytyy kontrollerista `MovieController` (`js/controller.js`). *Kontrolleriin* ei tarvitse tehdä mitään muutoksia.
