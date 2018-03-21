---
layout: exercise_page
title: "Tehtävä 2.4: Person (1p)"
exercise_template_name: W2E04.Person
exercise_discussion_id: 97783
exercise_upload_id: 380363
modified_at: 21.3.2018
---

Toteuta tehtäväpohjaan [Backbone-näkymän][Backbone-view] muodostin `PersonView` ja [Backbone-mallin][Backbone-model] muodostin `PersonModel` siten, että pohjassa valmiina oleva sivu näyttää latauduttuaan selaimessa seuraavalta:

[Backbone-view]: http://backbonejs.org/#View
[Backbone-model]: http://backbonejs.org/#Model

![Person UI](../img/w2e04-person.png "Person UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

Sivulla tulee olla myös tominnallisuus, joka kasvattaa sivun esittämän henkilön ikää, kun näkymän juurielementin sisältönä olevaa `div`-elementtiä klikataan.

Toteuta ratkaisu siten, että henkilön iän muuttuessa kaikki henkilön tiedot muodostetaan templaten avulla uudelleen osaksi dokumenttia.


**Palauta** tehtävän ratkaisuna tiedostot `PersonModel.js` ja `PersonView.js`.


{% comment %}



<h3>Sleepy? (3p)</h3>

<p>Tässä tehtävässä sinun tulee toteuttaa unipäiväkirja. Unipäiväkirjassa on kaksi toimintoa, unen lisääminen ja unistatistiikan listaaminen. Jokaisesta nukkumisesta kerätään alkukellonaika, loppukellonaika, ja freesiys (1-5). Pääsivu näyttää seuraavalta:</p>

<p><img src="img/w4e06-sleepy-1.png" border="1"/></p>

<p>Kun pääsivulta valitsee vaihtoehdon "Add entry", käyttäjälle näytetään seuraavanlainen näkymä.</p>

<p><img src="img/w4e06-sleepy-2.png" border="1"/></p>

<p>Näkymän voi täyttää normaalisti. Näkymän tulee tarkistaa, että freesiys-kenttään asetetaan numero, joka on väliltä 1-5.</p>

<p><img src="img/w4e06-sleepy-3.png" border="1"/></p>

<p>Kun unipäiväkirjaan lisätään tietue, käyttäjälle näytetään viesti "Thx!".</p>

<p><img src="img/w4e06-sleepy-4.png" border="1"/></p>

<p>Kun käyttäjä valitsee vaihtoehdon "Statistics", käyttäjälle näytetään näkymä, joka listaa tietueet. Näkymän lopussa tulostetaan freesiys-arvo, joka on keskiarvo kaikkien tietueiden sisältämistä arvoista.</p>

<p><img src="img/w4e06-sleepy-5.png" border="1"/></p>

<p>Huom! Toteuta tehtävä Backbonea käyttäen!</p>

<p>Vinkki! Voit iteroida kokoelmassa olevia yksittäisiä <em>malli</em>-olioita JQueryn .each-komennon avulla. Kun olet valmis ja sivusi toimii kuten pitää, palauta se TMC:lle.</p>


{% endcomment %}
