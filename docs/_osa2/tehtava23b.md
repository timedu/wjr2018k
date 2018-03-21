---
layout: exercise_page
title: "Tehtävä 2.3b: Model Counter (1p)"
exercise_template_name: W2E03B.ModelCounter
exercise_discussion_id: 97845
exercise_upload_id: 380448
modified_at: 21.3.2018
---

Toteuta tehtäväpohjaan kaksi [Backbone-näkymän][Backbone-view] muodostinfunktioa, `ListenerView` ja `SenderView`,  siten, että niillä muodostetut näkymät toteuttavat laskurin toiminnallisuuden
hyödyntäen pohjassa olevaa [Backbone-mallia][Backbone-model].

[Backbone-view]: http://backbonejs.org/#View
[Backbone-model]: http://backbonejs.org/#Model

![Model Counter UI](../img/w2e03b-model-counter.png "Model Counter UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

Näkymät ovat samarakenteisia [edellisen tehtävän](../tehtava23a) vastaavien kanssa:

~~~
    +---------------+    +---------------+
    | ListenerView  |    | SenderView    |
    +---------------+    +---------------+
    | el            |    | el            |
    | counter       |    +---------------+
    +---------------+    | events        |
    | initialize    |    +---------------+
    | render        |    
    +---------------+    
~~~

Tässä näkymät kommunikoivat mallin[^1] kautta:

[^1]: Näkymät muodostetaan tässä siten, että malli näkyy niissä muttujassa `this.model` (ks. `index.html`).

~~~
+--------------+  on/change  +--------------+   inc   +------------+
| listenerView |------------>| counterModel |<--------| senderView |
+--------------+ get/counter +--------------+         +------------+
~~~

Kun näkymä `listenerView` luodaan (`initialize`), se asetetaan kuuntelemaan mallin (`counterModel`) `change`-tapahtumia. Tapahtuman sattuessa näkymä lukee ([get][get]) mallista   laskurinsa arvon ja asettaa sen dokumentiin.

[get]: http://backbonejs.org/#Model-get

Kun näkymään `senderView` liittyvää painiketta klikataan, näkymä kutsuu malliin määriteltyä `inc`-metodia, joka kasvattaa mallin `counter`-kentän arvoa yhdellä (ks. `js/CounterModel.js`).

**Palauta** tehtävän ratkaisuna tiedostot `ListenerView.js` ja `SenderView.js`.

<br/>
