---
layout: exercise_page
title: "Tehtävä 2.5: Clock (1p)"
exercise_template_name: W2E05.Clock
exercise_discussion_id: 97784
exercise_upload_id: 380364
modified_at: 21.3.2018
---

Laadi tehtäväpohjaan [Backbone-näkymän][Backbone-view] muodostinfunktio, `ClockView`,  siten, että sillä muodostettu näkymä toteuttaa kellon toiminnallisuuden pohjassa valmiina olevan [Backbone-mallin][Backbone-model] kanssa. Sovelukseen liittyvä sivu näyttää alkutilanteessa seuraavalta:

[Backbone-view]: http://backbonejs.org/#View
[Backbone-model]: http://backbonejs.org/#Model

![Clock UI](../img/w2e05-clock.png "Clock UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

Kello käynnistyy, kun sen sivulla olevaa käyttöliittymää klikataan. Kellon ollessa käynnissä sen lukema kasvaa yhdellä sekunnin välein. Kun käynnissä olevaa kelloa klikataan, se pysähtyy ja kellon lukemaksi jää käynnissäolon aikana muodostunut arvo. Kun pysähtynyttä kelloa klikataan uudelleen, lukeman askellus jatkuu siitä, mihin se pysäyttämisen yhteydessä jäi.

Näkymä ja malli ovat ranteeltaan seuraavanlaisia:

~~~
    +---------------+    +---------------+    +----------------+
    | ClockView     |    | ClockModel    |    | Backbone.Model |
    +---------------+    +---------------+    +----------------+  
    | el            |    | time          |---<| toJSON()       |
    +---------------+    +---------------+    +----------------+
    | initialize()  |    | incTime()     |
    | template()    |    +---------------+
    | render()      |    
    +---------------+   
    | events        |    
    +---------------+   

~~~

Toteuta ratkaisu siten, että käyttöliittymän päivitys perustuu mallin sisällön muutoksiin (*on/change*) ja niin, että se tapahtuu aina templaten avulla.

~~~
+-----------+     on/change     +------------+
| clockView |------------------>| clockModel |
+-----------+   incTime,toJSON  +------------+
~~~

Oiva apuväline sekunnin välein tapahtuvaan askellukseen on [setInterval][setInterval]-funktio, jolla käynnistetyn askelluksen voi pysäyttää  funktiolla [clearInterval][clearInterval].

[setInterval]: https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval

[clearInterval]: https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearInterval


**Palauta** tehtävän ratkaisuna tiedosto `ClockView.js`.




{% comment %}

<h3>Tasks (3p)</h3>

Toteuta sovellus tehtävien hallintaan. Kunkin tehtävän tulee sisältää tieto `id` eli tunnus, `title` eli otsikko, ja `completed` eli onko tehtävä tehty. Tehtäviä hallinnoivan kokoelmaolion tulee hakea tehtävät palvelimelta osoitteesta <http://pure-escarpment-3768.herokuapp.com/app/tasks>. Sovelluksesi tulee pystyä myös lisäämään ja muokkaamaan tehtäviä.

<p>Kun sovellus käynnistyy, sen tulee hakea olemassaolevat tehtävät. Alla olevassa kuvassa tehtäviä on 4, ja yhtäkään niistä ei ole merkattu tehdyksi.</p>

<p><img src="img/w4e07-tasks-1.png" border="1"/></p>

<p>Toteuta sovellukseen toiminnallisuus, jonka avulla tehtävän tila (completed) muuttuu sitä klikattaessa. Kun tehtävää klikataan, tilan tulee päivittyä myös palvelimelle. Alla kaksi tehtävää on merkattu tehdyiksi. Huom! Tehtäviä tulee pystyä merkitsemään myös tekemättömiksi.</p>

<p><img src="img/w4e07-tasks-2.png" border="1"/></p>  

<p>Tehtävien lisäyksen tulee tapahtua tekstikentän kautta.</p>

<p><img src="img/w4e07-tasks-3.png" border="1"/></p>

<p>Tehtävä lisätään, kun käyttäjä painaa enteriä. (keycode 13)</p>

<p><img src="img/w4e07-tasks-4.png" border="1"/></p>

<p>Huom! Toteuta tehtävä Backbonea käyttäen!</p>

<p>Kun sovelluksesi toimii kuten toivottu, lähetä se TMC:lle.</p>

{% endcomment %}
