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





{% comment %}

Toteuta tehtäväpohjaan Backbone.js:n avulla malli `Person`, joka sisältää attribuutit `name`, `age` ja `abilities`. Mallin tulee olla muuttujan `site.model` sisällä, ja sen attribuutin `abilities` tulee olla lista. Toteuta malli siten, että sen voi luoda seuraavasti:

<pre class="sh_javascript_dom">
var mikke = new site.model.Person("mikke", 28, ["Coding", "Music", "Reproduction"]);
</pre>

Lisää tehtäväpohjassa valmiina olevalle näkymälle tapahtuma: kun elementtiä, johon malli on renderöity, klikataan, mallin iän arvon tulee kasvaa yhdellä (attribuutin age arvon tulee kasvaa yhdellä), jonka jälkeen näkymä renderöidään uudestaan.

Luo näkymä kun sivu on ladattu. Alla on esimerkkejä näkymän sivulle luomasta tekstistä. Ensimmäisessä kuvassa elementtiä ei ole klikattu kertaakaan, toisessa kuvassa elementtiä on klikattu 4 kertaa.


<p><img src="img/w4e04-hellomodel-0.png" border="1"/></p>
<p><img src="img/w4e04-hellomodel-2.png" border="1"/></p>

<p>Kun sivusi toimii halutusti, palauta se TMC:lle.</p>

{% endcomment %}
