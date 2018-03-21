---
layout: exercise_page
title: "Tehtävä 2.2: Template Counter (1p)"
exercise_template_name: W2E02.TemplateCounter
exercise_discussion_id: 97781
exercise_upload_id: 380361
modified_at: 21.3.2018
---

Toteuta tehtäväpohjaan templateen tukeutuva laskurin sisältävä [Backbone][Backbone]-näkymän muodostinfunktio `CounterView`. Näkymä liittyy seuraavanlaiseen dokumenttiin (`index.html`), joka on tehtäväpohjassa valmiina:

[Backbone]: http://backbonejs.org/#View

![Template Counter UI](../img/w2e02-template-counter.png "Template Counter UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

Selaimessa esitettavä dokumentti poikkeaa [edellisen tehtävän](../tehtava21) ratkaisusta siten, että se ei sisällä erillistä painiketta. Tässä laskuri kasvaa klikkaamalla sivulla olevaa laskurin arvon ja sen otsikon sisältävää `div`-elementtiä.

[Edellisen tehtävään](../tehtava21) verrattuna tässä näkymällä on uusi metodi, `template`:


~~~
    +---------------+
    | CounterView   |
    +---------------+
    | el            |
    | counter       |
    +---------------+
    | initialize    |
    | template      |
    | render        |
    +---------------+
    | events        |
    +---------------+
~~~

`render` käyttää tehtäväpohjassa valmiina olevaa `template`-metodia[^1] esittäessään laskurin arvon dokumentissa.

[^1]: Tässä tukeudutaan [Handlebars][Handlebars]-sivupojiin; ks. [Backbone.js and Handlebars.js example][Backbone-Handlebars-example].

[Handlebars]: http://handlebarsjs.com
[Backbone-Handlebars-example]: https://gist.github.com/kyleondata/3440492


**Palauta** tehtävän ratkaisuna tiedosto `CounterView.js`.

<br/>
