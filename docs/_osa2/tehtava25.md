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
