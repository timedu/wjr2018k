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
