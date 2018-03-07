---
layout: exercise_page
title: "Tehtävä 1.2 Puhelinmuistio - \"Class\" (3p)"
exercise_template_name: W1E02.PuhClass
exercise_discussion_id: 96765
exercise_upload_id: 378567
modified_at: 7.3.2018
---

Toteuta [edellistä tehtävää](../tehtava11) vastaava ratkaisu käyttäen kuitenkin *ECMAScript 2015* -standandin määrittelemää luokkanotaatiota.

**Palauta** tehtävästä `Puhelinmuistio`-luokkamäärityksen sisältävä tiedosto `puhelinmuistio.js`. Varmista ennen palauttamista, että tehtäväpohjan sisältämät testit menevät läpi ilman virheilmoituksia.

### Vihjeitä ja lisätietoja

Seuraavassa on [eräältä MDN:n sivulta](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) poimittu esimerkki luokan määrittelystä:

{% highlight js %}

class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  // Method
  calcArea() {
    return this.height * this.width;
  }
}
const square = new Rectangle(10, 10);

{% endhighlight %}

<small>Listaus 1.</small>

Edellinen vastaa seuraavaa:

{% highlight js %}

funktion Rectangle {
    this.height = height;
    this.width = width;
}
Rectangle.prototype.calcArea = function() {}
  return this.height * this.width;
}
const square = new Rectangle(10, 10);

{% endhighlight %}

<small>Listaus 2.</small>

Ainoastaan notaatiot poikkeavat toisistaan.
