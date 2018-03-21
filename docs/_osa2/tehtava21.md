---
layout: exercise_page
title: "Tehtävä 2.1: Counter (2p)"
exercise_template_name: W2E01.Counter
exercise_discussion_id: 97780
exercise_upload_id: 380359
modified_at: 21.3.2018
---

Toteuta tehtäväpohjaan laskurin sisältävä [Backbone][Backbone]-näkymän muodostinfunktio `CounterView`. Lähtötilanteessa laskurin arvo on 0. Kun sivulla olevaa painiketta klikataan, laskurin arvo kasvaa yhdellä ja arvo esitetään dokumentissa.

[Backbone]: http://backbonejs.org/#View

![Counter UI](../img/w2e01-counter.png "Counter UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

Tehtäväpohjassa valmiina oleva sivu `index.html` luo näkymän tässä tiedostoon `js/todo/CounterView.js` laadittavan muodostimen avulla. Toteuta muodostin siten, että se noudattaa seuraavaa rakennetta:

~~~
    +---------------+
    | CounterView   |
    +---------------+
    | el            |
    | counter       |
    +---------------+
    | initialize    |
    | render        |
    +---------------+
    | events        |
    +---------------+
~~~

`el` sisältää näkymän juurielementin dokumentissa. Muuttujassa `counter` ylläpidetään laskurin arvoa. Funktio `initialize` asettaa näkymän alkutilaan. `render`[^2] päivittää laskurin arvon dokumentiin. `events` määrittelee tapahtuman, jonka seurauksena laskurin arvoa on kasvatettava yhdellä.

[^2]: Toteuta `render` siten, että se viittaa dokumentiin funktiolla `this.$`: [jQuery][jQuery]-funktio, joka käsittelee ainoastaan juurielementin määritelemää aluetta dokumentista.

[jQuery]: https://jquery.com

**Palauta** tehtävän ratkaisuna tiedosto `CounterView.js`.

<br/>
