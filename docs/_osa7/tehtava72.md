---
layout: exercise_page
title: "Tehtävä 7.2: Puhelinluettelo - frontend (1p)"
exercise_template_name: w7e02.puhelinluettelo-frontend
exercise_discussion_id: 100544
exercise_upload_id: 384889
modified_at: 15.5.2018
---

{% assign fullstack = "https://fullstackopen.github.io" %}

Ratkaise [Full stack open 2018]({{fullstack}}) materiaalin tehtävä

&nbsp; &nbsp; [(3.9) Frontend käyttää backendiä ]({{fullstack}}/tehtävät#39-puhelinluettelon-backend-osa-9)  

Tässä voi lähteä liikkeelle [Tehtävä 6.2](../../osa6/tehtava62) ratkaisusta (frontend) kopioimalla sen osaksi [edellisen tehtävän](../tehtava71) yhteydessä laaditun backendin. Tehtäväpohja ehdottaa seuraavanlaista rakennetta:

~~~~
[backend]
    [node_modules]
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

Kansiorakenne sekä tiedostot `package.json` (frontend) ja `src/index.js` ovat pohjassa valmiina.

Käy ennen tehtävän ratkaisua läpi materiaalin kohta [Yhteys frontendiin]({{fullstack}}/osa3/#yhteys-frontendiin).


**Palauta** tehtävästä tiedostot `backend/package.json`, `backend/server.js` sekä `src/services/persons.js`.

