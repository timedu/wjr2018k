---
layout: exercise_page
title: "Tehtävä 7.4: Puhelinluettelo - fullstack (7p)"
exercise_template_name: # w7e04.puhelinluettelo-fullstack
exercise_discussion_id: 100546
exercise_upload_id: 384891
modified_at: 16.5.2018
---

{% assign fullstack = "https://fullstackopen.github.io" %}

Ratkaise [Full stack open 2018]({{fullstack}}) materiaalin tehtävät

&nbsp; &nbsp; [(3.13) Vaihe 1: Kaikki numerot]({{fullstack}}/tehtävät#313-puhelinluettelo-ja-tietokanta-osa-1)   
&nbsp; &nbsp; [(3.14) Vaihe 2: Formatointi]({{fullstack}}/tehtävät#314-puhelinluettelo-ja-tietokanta-osa-2)   
&nbsp; &nbsp; [(3.15) Vaihe 3: Uusi numero]({{fullstack}}/tehtävät#315-puhelinluettelo-ja-tietokanta-osa-3)   
&nbsp; &nbsp; [(3.16) Vaihe 4: Numeron poisto]({{fullstack}}/tehtävät#316-puhelinluettelo-ja-tietokanta-osa-4)   
&nbsp; &nbsp; [(3.17) Vaihe 5: Numeron muutos]({{fullstack}}/tehtävät#317-puhelinluettelo-ja-tietokanta-osa-5)   
&nbsp; &nbsp; [(3.18) Vaihe 6: Yksi numero ja info]({{fullstack}}/tehtävät#318-puhelinluettelo-ja-tietokanta-osa-6)   
&nbsp; &nbsp; [(3.19) Vaihe 7: Duplikaatin esto]({{fullstack}}/tehtävät#319-puhelinluettelo-ja-tietokanta-osa-7)   


Tehtävässä ei ole mukana pohjakoodia. Liikkeelle voi lähteä  [Tehtävän 7.2](../tehtava72) ratkaisusta, jossa *frontend* ja *backend* ovat samassa työhakemistossa. *backend*  edellyttää muokkaamista. Täydennykset voi toteuttaa esim. hakemistoon `backend/todo` seuraavanlaisesti:

~~~~
[backend]
    [node_modules]
    [todo]
        [models]
            db-config.js
            person.js
        server-1.js
        server-2.js
        ...
        server-7.js
    index.js
    package.json
    server.js
[node_modules]
[public]
[src]
    [components]
        Filter.js
        NewPerson.js
        Person.js
    [services]
        persons.js
    App.js
    index.css
    index.js
package.json    
~~~~

Ehdotuksessa `backend/index.js` on *backendin* päämoduuli, joka käyttöönsä ratkaisun vaihetta edustavan moduulin:

{% highlight js %}

require('./server')
// require('./todo/server-1')
// require('./todo/server-2')
// ...
// require('./todo/server-7')

{% endhighlight %}

`backend/server.js` edustaa tässä lähtökohtana olevaa [Tehtävän 7.2](../tehtava72) *backend*-osuuden ratkaisua. Tietokannan *url* on määritelty [edellisen tehtävän](../tehtava73) tapaan tiedostoon `db-config.js`, jonka tässä laadittava *model*-moduuli (`person.js`) ottaa käytöönsä:

{% highlight js %}

const mongoose = require('mongoose')
const url = require('./db-config')
mongoose.connect(url)
...

{% endhighlight %}

Tietokantaa hyödyntävä *REST*-rajapinnan toteuttava moduuli ottaa sitten käyttöönsä *model*-moduulin:

{% highlight js %}

...
const Person = require('./models/person')
...

{% endhighlight %}


Käy ennen tehtävien ratkaisua läpi materiaalin
[kolmas osa]({{fullstack}}/osa3/) - erityisesti kaikki tietokannan käsittelyä käsittelevät kohdat.

Laadi ratkaisu kumulatiivisesti siten, että seuraavan vaiheen ratkaisu sisältää myös edellisten vaiheiden ratkaisut. 

**Palauta** tehtävästä tiedosto `person.js` sekä yksi tiedostoista `server-1.js` - `server-7.js` riippuen siitä, mihin vaiheeseen asti ratkaisua olet vienyt.

