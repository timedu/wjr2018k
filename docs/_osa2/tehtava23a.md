---
layout: exercise_page
title: "Tehtävä 2.3a: Message Counter (1p)"
exercise_template_name: W2E03.MessageCounter
exercise_discussion_id: 97782
exercise_upload_id: 380362
modified_at: 21.3.2018
---

Toteuta tehtäväpohjaan kaksi [Backbone-näkymän][Backbone-view] muodostinfunktioa, `ListenerView` ja `SenderView`,  siten, että niillä muodostetut näkymät toteuttavat yhdessä laskurin toiminnallisuuden kommunikoiden keskenään [Backbone-tapahumien][Backbone-event] avulla. Näkymät liittyvät seuraavanlaiseen dokumenttiin (`index.html`), joka on tehtäväpohjassa valmiina:

[Backbone-view]: http://backbonejs.org/#View
[Backbone-event]: http://backbonejs.org/#Events

![Message Counter UI](../img/w2e03-message-counter.png "Message Counter UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

`SerderView` liittyy dokumentissa olevaan painikkeeseen ja `ListenerView` alueeseen, joka sisältää laskurin arvon esittävän `span`-elementin. Näkymillä on seuraavalainen rakenne:

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

Viestinvälittäjänä voidaan käyttää `Backbone`-objektia[^msg-example]:

[^msg-example]: Esimerkki tästä löytyy kirjoituksesta [Communicating between views in Backbone][msg-example] kohdasta *3. Using Backbone as the event bus*.

[msg-example]: https://veerasundar.com/blog/2013/04/communicating-between-views-in-backbone/   

~~~
+--------------+     on      +----------+   trigger   +------------+
| listenerView |------------>| Backbone |<------------| senderView |
+--------------+  increment  +----------+  increment  +------------+
~~~

Kun näkymä `listenerView` luodaan (`initialize`), se asetetaan kuuntelemaan ([on][on]) `Backbone`-objektiin liittyviä `increment`-tapahtumia. Tapahtuman sattuessa näkymä kasvattaa laskurinsa arvoa yhdellä ja asettaa päivitetyn arvon dokumentiin.

[on]: http://backbonejs.org/#Events-on

Kun näkymään `senderView` liittyvää painiketta klikataan, näkymä asettaa ([trigger][trigger])  `Backbone`-objektille `increment`-tapahtuman.

[trigger]: http://backbonejs.org/#Events-trigger

**Palauta** tehtävän ratkaisuna tiedostot `ListenerView.js` ja `SenderView.js`.

<br/>
