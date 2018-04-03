---
layout: exercise_page
title: "Tehtävä 3.5: Laskin"
exercise_template_name: W3E05.Laskin
exercise_discussion_id: 98575
exercise_upload_id: 381429
modified_at: 3.4.2018
---

Muokkaa tehtäväpohjan `todo`-kansiossa olevia tiedostoja siten, että käyttäjä voi laskea kokonaislukujen  yhteen-, vähennys-, kerto- ja jakolaskuja. Laskenta suoritetaan syöttämällä luvut kahteen kenttään ja painamalla jotain neljästä painikkeesta, jolloin valittu laskuoperaatio suoritetaan ja tulos näytetään kenttien alapuolella.

Jos käyttäjä yrittää jakaa lukua nollalla, ota jakolaskupainike pois käytöstä ([ng-disabled][ng-disabled]).
Laskimen kaikki painikkeet ovat pois käytöstä, jos ainakin toinen laskutoimituksen operandeista ei ole kelvollinen kokonaisluku.

[ng-disabled]: https://docs.angularjs.org/api/ng/directive/ngDisabled

**Palauta** tehtävästä tiedostot `template.html` ja `controller.js`, joiden rungot löytyvät `todo`-hakemistosta. Varmista, että tehtäväpohjassa olevat testit menevät läpi ennen palautusta.

### Lisätietoja

Tehtävä on lähes sama kuin lähteen
[Tehtävä 31][tehtävä-31], jonka edellä materiaalissa käsitellään tehtävän ratkaisua tukevia asioita.

[tehtävä-31]: http://web-selainohjelmointi.github.io/#vk-4-t31

Tehtäväpohjassa on määritelty [säännölliset lausekkeet][Regular_Expressions], joita voi hyödyntää painikkeiden aktivoinnissa:

[Regular_Expressions]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions

{% highlight javascript %}

    var LUKU = /^\s*[0-9]{1,}\s*$/;
    var NOLLA = /^\s*0{1,}\s*$/;

{% endhighlight %}

Säännöllisen lausekkeen [test][test] -metodin avulla voidaan tutkia, sopiiko jokin merkkijono lausekkeen määrittelemään malliin, esim.

[test]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test

{% highlight javascript %}

    LUKU.test('123X');  // false
    LUKU.test('123');   // true
    NOLLA.test(' 00 '); // true

{% endhighlight %}
