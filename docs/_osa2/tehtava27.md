---
layout: exercise_page
title: "Tehtävä 2.7: Taskit (3p)"
exercise_template_name: W2E07.Taskit
exercise_discussion_id: 97786
exercise_upload_id: 380366
modified_at: 22.3.2018
---

Toteuta sovellus tehtävien hallintaan. Tehtävä sisältää seuraavat tiedot: `id`, `title` ja `completed`.

Sovelluksen käynnistyessä selaimeen tulee esille tekstikentän sisältävä dokumentti:  

![Taskit UI](../img/w2e07-taskit-1.png "Taskit UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 1.</small>

Kun käyttäjä syöttää kenttään tehtävän otsikon ja painaa *enter*-näppäintä, tehtävä talletetaan sovelluksen sisältämään Backbone-kokoelmaan, minkä jälkeen kokoelman sisältämät tehtävät päivitetään selaimessa olevaan dokumentiin.

![Taskit UI](../img/w2e07-taskit-2.png "Taskit UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 2.</small>

Käyttäjä voi vaihtaa tehtävän tilaa (completed - true/false) klikkaamalla dokumentissa ao. tehtävään liittyvää `p`-elementtiä.

Sovellukseen sisältyy [Backbone-mallin][Backbone-model] muodostin `TaskCollection` sekä kaksi [Backbone-näkymien][Backbone-view] muodostinta, `AddTaskView` ja `ListTasksView`. Mallin muodostin on tehtäväpohjassa valmiina.

Näkymät luodaan tehtäväpohjassa (ks. `index.html`) siten, että kokoelma näkyy niissä muuttujassa `this.collection`.

[Backbone-view]: http://backbonejs.org/#View
[Backbone-model]: http://backbonejs.org/#Model

Toteuta ratkaisu seuraavan periaatteen mukaan:

![Diagram](../img/w2e07-diagram.png "Diagram"){: style="display: block; margin: auto; margin-top: 10px; width: 600px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kaavio 1.</small>


Näkymä `addTaskView` tallettaa kokoelmaan `taskCollection` uuden tehtävän, jonka `title` saadaan dokumentissa olevasta tekstikentästä. Tehtävän `completed`-attribuutin arvoksi asetetaan `false` ja `id`-attribuutin arvoksi kokoelman sisältämien mallien lukumäärä ([length][length]). Siten ensimmäisen tehtävän id:ksi muodostuu 0. Talletus suoritetaan, kun kursorin ollessa dokumentin `input`-kentässä painetaan *enter*-näppäintä. Tästä aiheutuu [keypress][keypress]-tapahtuma, johon liittyvän tapahtumaobjektin `keyCode`-attribuutista löytyy painetun näppäimen koodi. *enter*-näppäimen tapauksessa se on `13`.

[length]: http://backbonejs.org/#Collection-length
[keypress]: https://developer.mozilla.org/en-US/docs/Web/Events/keypress

Näkymää `listTaskView` muodostettaessa (`initialize`) se asetetaan kuuntelemaan ([on][on]) kokoelmaan `taskCollection` kohdistuvia lisäyksiä (*add*) ja muutoksia (*change*), joihin näkymä reagoi päivittämällä kokoelman sisällön dokumenttiin. Data saadaan haettua kokoelman [toJSON][toJSON]-metodilla. Näkymä suorittaa sivun päivityksen templaten avulla, minkä seurauksena tehtäviin liittyvät tiedot esitetään dokumentissa `p`-elementeissä (ks. `index.html`). Tehtävän `id` asettuu elementin `data-id`-attribuutin arvoksi.

[on]: http://backbonejs.org/#Events-on
[toJSON]: http://backbonejs.org/#Collection-toJSON

Näkymän `listTaskView` kautta tapahtuu myös tehtävän tilan muutos, mikä käynnistyy käyttäjän klikattua tehtävään liittyvää `p`-elementtiä. Tehtävän `id` löytyy [click][click]-tapahtumaan liittyvän objektin ominaisuudesta `target.`[`dataset`][dataset]`.id`. Muutoksen kohteena oleva malli voidaan etsiä kokoelmasta sen [findWhere][findWhere]-metodilla. Mallista `completed`-kentän nykyinen arvo voidaan lukea mallin [get][get]-metodilla ja kentälle voidaan asettaa uusi arvo [set][set]-metodilla[^elegantimpi].



[^elegantimpi]:  Elegantimpi ratkaisu tämän osalta voisi olla sellainen, että malliin olisi määritelty tehtävän tilan vaihtava metodi, jota näkymä käyttäisi `get`/`set`-metodien sijaan.

[click]: https://developer.mozilla.org/en-US/docs/Web/Events/click
[dataset]: https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/dataset
[findWhere]: http://backbonejs.org/#Collection-findWhere
[get]: http://backbonejs.org/#Model-get
[set]: http://backbonejs.org/#Model-set

**Palauta** tehtävän ratkaisuna tiedostot  `AddTaskView.js` ja `ListTasksView.js`.

<br/>
