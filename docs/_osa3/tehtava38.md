---
layout: exercise_page
title: "Tehtävä 3.8: Slider (3p)"
exercise_template_name: W3E08.Slider
exercise_discussion_id: 98578
exercise_upload_id: 381432
modified_at: 5.4.2018
---

Toteuta tehtäväpohjaan [jQueryUI][jQueryUI]-kirjaston [slider][slider]-widgetti *slider*-nimisenä AngularJS-[direktiivinä][directive].

[jQueryUI]: https://jqueryui.com
[slider]: https://jqueryui.com/slider/
[directive]: https://docs.angularjs.org/guide/directive

![Slider](../img/slider.png "Slider"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px;"}

Kun käyttäjä muuttaa sliderin arvoa klikkaamalla tai vetämällä, myös siihen *ng-model* -direktiivin avulla sidotun muuttujan arvo muuttuu. Sliderin alkuarvon tulee olla sama, kuin siihen sidotun muuttujan arvo. Sliderin ääripäät vastaavat lukuarvoja 0 ja 100. Pohjassa valmiina olevassa templatessa (`index.html`) div-elementtiin sidottu slider-direktiivi näyttäää seuraavalta:


{% highlight html %}

<div slider ng-model="number"></div>

{% endhighlight %}


**Palauta** tehtävän ratkaisuna tiedosto `slider_directive.js`, jonka runko löytyy projektipohjan `todo`-hakemistosta.

### Lisätietoja

Tehtävä on lähes sama kuin lähteen [Tehtävä 34][tehtävä-34], jonka edellä materiaalissa käsitellään tehtävän ratkaisua tukevia asioita.

[tehtävä-34]: http://web-selainohjelmointi.github.io/#vk-4-t34

Kattava dokumentaatio *slider*-widgetistä löytyy sen [käsikirja-sivulta](http://api.jqueryui.com/slider/).
