---
layout: collection_index
permalink: /:collection/index.html
modified_at: 8.3.2018
---

JavaScript-ohjelmissa käsitellään oliota, vaikka kieli ei sisällä Java-kielen kaltaisia luokkia. Oliot eivät kapseloi ominaisuuksiaan, mutta modulointiin on käytettävissä kielessä muita mekanismeja. Kurssin ensimmäisessä osassa tarkastellaan hieman JavaScriptin piirteitä, jotka poikkeavat selvästi esim. Java-kielestä.

### Tehtävät

Tämä osa sisältää viisi tehtävää, joiden kaikkien ratkaisuna on ulospäin samalla tavalla toimiva puhelinmuistio-sovellus. Tehtävien pohjakoodissa käyttöliittymän merkkaus on valmiina. Tehtävistä neljässä ensimmäisessä laadittavana on puhelinmuistion dataa ylläpitävä olio eri periaatteilla toteutettuna. Näissä myös käyttöliittymää käsittelevä ohjelmakoodi on täysin valmiina.
Viimeisessä tehtävässä  soveluksen koodi jäsentyy muihin verrattuna kokonaisuutena hieman toisella tavalla.

{% include exercises_list.md %}

[Tehtävässä 1.1](tehtava11) laaditaan muodostinfunktio, jolla luodut oliot eivät kapseloi dataa. Metodit sijoitetaan muodostimen `prototype` -olion ominaisuuksiksi. [Tehtävässä 1.2](tehtava12) toteutetaan ominaisuuksiltaan edellistä tehtävää vastaava ratkaisu käyttäen kuitenkin JavaScriptin tuoretta luokka-notaatiota. [Tehtävässä 1.3](tehtava13) rakennetaan määrittelyn yhteydessä suoritettava funktio, joka luo kapseloitua muistio-dataa käsittelevän olion. [Tehtävän 1.4](tehtava14) funktiolla voidaan muodostaa useita samarakenteisia datan kapseloivia puhelinmuistio-olioita. [Tehtävässä 1.5](tehtava15) laaditaan sovelluksesta MVC-mallin mukaan jäsentyvä ratkaisu siten, että jokaiselle MVC-mallin elementtille (Model, View, Controller) on oma muodostinfunktionsa.

Tehtävät ovat modifikaatioita *Web-selainohjelmointi* -lukemiston
[tehtävästä 17](http://web-selainohjelmointi.github.io/#vk-2-t17).

### Lisätietoja

Tämän osan tehtävissä esillä olevia JavaScriptin olioita ja moduuleja käsitellään
Helsingin yliopiston *Web-selainohjelmointi* -materiaalin luvuissa
[6. Lisää JavaScriptistä](http://web-selainohjelmointi.github.io/#6-Lisää-JavaScriptistä)
ja
[8. Oliot ja Moduulit](http://web-selainohjelmointi.github.io/#8-Oliot-ja-Moduulit).
Luku
[9. MV* ja Web-sovelluksen rakenne](http://web-selainohjelmointi.github.io/#9-MV*-ja-Web-sovelluksen-rakenne)
esittelee erilaisten MVC -mallien JavaScript-toteutuksia.

[MDN:n][mdn] sivustolla on kattava [JavaScript-materiaali][mdn-js]. Jos kieli ei ole aivan lähimuistissa, sivustolta voi poimia luettavaksi sivun [A re-introduction to JavaScript](https://developer.mozilla.org/bm/docs/Web/JavaScript/A_re-introduction_to_JavaScript).

[mdn]: https://developer.mozilla.org/fi/docs/Web
[mdn-js]: https://developer.mozilla.org/bm/docs/Web/JavaScript

*Udacity:ssä* voi opiskella (veloituksetta) johdanto-tason yläpuolelle asettuvia verkkokursseja
[Object-Oriented JavaScript][ud015] ja [ES6 - JavaScript Improved][ud356].

[ud015]: https://eu.udacity.com/course/object-oriented-javascript--ud015
[ud356]: https://eu.udacity.com/course/es6-javascript-improved--ud356


{% comment %}

* <http://speakingjs.com/es5/index.html>
* <http://exploringjs.com/es6/index.html>

{% endcomment %}
