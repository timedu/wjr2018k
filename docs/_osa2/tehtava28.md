---
layout: exercise_page
title: "Tehtävä 2.8: Taskit Rest (2p)"
exercise_template_name: W2E08.TaskitRest
exercise_discussion_id: 97787
exercise_upload_id: 380367
modified_at: 22.3.2018
---

Laadi [edellisen tehtävän](../tehtava27) ratkaisun kaltainen sovellus kuitenkin nyt niin, että se käyttää tehtävien tallettamiseen [REST][REST]-rajapinnan tarjoavaa web-palvelua.

[REST]: https://en.wikipedia.org/wiki/Representational_state_transfer

Web-palvelu[^huom-node] on tehtäväpohjassa valmiina (`restApp.js`). Kun palvelun käynnistää ja tekee selaimella pyynnön osoitteeseen `http://localhost:3000/tasks`, selaimen ikkunaan pitäisi ilmestyä seuraavanlainen näkymä:

[^huom-node]: Palvelu on [node][node]-sovellus ja siten sen käynnistäminen edellyttää, että node on asennettu kehitysympäristöön. Toinen edellytys on, että ympäristöön on asennettu sovelluksen edellyttämät ulkopuoliset moduulit. Nämä asentuvat npm:llä: klikkaa NetBeansissa hiiren oikealla näppäimellä projektia ja ota esiin tulevasta valikosta valinta *npm install*.

[node]: https://nodejs.org/en/

![Taskit ](../img/w2e08-taskit-rest-json.png "Taskit JSON"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 1.</small>

Rakennettava sovellus esittää nämä tiedot seuraavasti pyynnöllä osoitteeseen `http://localhost:3000/`:

![Taskit UI](../img/w2e08-taskit-rest.png "Taskit UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 2.</small>

Tässä sovellus toimii ulospäin aivan samoin kuin [edellisen tehtävän](../tehtava27) ratkaisu. Sisäinen rakenne on kuitenkin hivenen erilainen:

![Diagram](../img/w2e08-diagram.png "Diagram"){: style="display: block; margin: auto; margin-top: 10px; width: 600px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kaavio 1.</small>

Tarvittavat muutokset on esitetty edellä olevassa kaaviossa vahvennetulla tekstillä: [url][url], [create][create], [save][save], [sync][sync].   

[sync]: http://backbonejs.org/#Events-catalog
[url]: http://backbonejs.org/#Collection-url
[create]: http://backbonejs.org/#Collection-create
[save]: http://backbonejs.org/#Model-save

**Palauta** tehtävän ratkaisuna tiedostot  `AddTaskView.js`, `ListTasksView.js` ja `TaskCollection.js`.

<br/>
