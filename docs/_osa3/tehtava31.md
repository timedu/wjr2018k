---
layout: exercise_page
title: "Tehtävä 3.1: James Bond"
exercise_template_name: W3E01.JamesBond
exercise_discussion_id: 98571
exercise_upload_id: 381425
modified_at: 3.4.2018
---

Muokkaa tehtäväpohjaa siten, että näkymän otsikon sisältö määräytyy "*etunimi*"- ja "*sukunimi*"-tekstikenttien perusteella. Jos esim. "*etunimi*"-kentän arvo on "*Karri*" ja "*sukunimi*"-kentän arvo on "*Veto*", on otsikon sisältö "*My names is Veto, Karri Veto*". Otsikon alkuarvon tulee olla "*My name is Bond, James Bond*".

**Palauta** tehtävästä tiedostot `template.html` ja `controller.js`. Varmista, että tehtäväpohjassa olevat testit[^2] menevät läpi ennen palautusta.

[^2]: Huom. Älä poista templatessa olevia `id`-attribuutteja, koska testit käyttävät näitä elementtien paikannuksessa.

### Lisätietoja

Tämä tehtävä on lähes sama kuin lähteen [Tehtävä 27](http://web-selainohjelmointi.github.io/#vk-4-t27), jonka edellä käsitellään tehtävän ratkaisua tukevia asioita.

Tehtäväpohjan tietostot on jäsennetty NetBeans-projektissa seuraavasti:

~~~
index.html
[todo]
   template.html
   controller.js
[test]
   SpecRunner.html
   [spec]
      SpecApp.js
~~~

`index.html` integroi sovelluksen siten, että se sisällyttää osakseen täydentävää merkkausta (`template.html`) ja ohjelmakoodia (`controller.js`), jotka löytyvät projektin `todo`-hakemistosta[^1]. Testaukseen liittyvät tiedostot sijaitsevat `test`-hakemistossa.

[^1]: Projektin `todo`-hakemisto sisältää tiedostorunkoja, jotka palautetaan täydennettynä tehtävän ratkaisuna.

Tiedosto `index.html` on pohjassa valmiina. Merkkauksessa on viite
 [AngularJS](https://angularjs.org) -kirjastoon, joka otetaan käyttöön verkon yli.

{% highlight html %}

<!DOCTYPE html>
<html>
    <head>
        <title>My name is Bond, James Bond</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
    </head>
    <body ng-app='BondApp'>
        <div ng-include="'./todo/template.html'" /></div>        
        <script src='./todo/controller.js'></script>
    </body>
</html>

{% endhighlight %}

Merkkauksen viitaama `template.html` otetaan tässä käyttöön AngularJS:n `ng-include` -direktiivillä. Viitatun tiedoston sisältö tulee `div` -elementin sisällöksi. `controller.js` on rakennettu pohjassa hieman eri tavalla kuin mitä on esitetty lähteen ao. luvun alkupuolella, mutta sen toiminnassa ei ole rakenteellisesta eroavaisuudesta huolimatta eroa.


<br/>
