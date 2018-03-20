---
layout: exercise_page
title: "Tehtävä 2.2: Template Counter (1p)"
exercise_template_name: #
exercise_discussion_id: #
exercise_upload_id: #
kesken:  1
no_review: 1
julkaisu: 21.3.2018
---

Tehtävä 2.2

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
