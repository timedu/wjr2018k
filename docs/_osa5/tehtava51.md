---
layout: exercise_page
title: "Tehtävä 5.1: HalfStack (5p)"
exercise_template_name: w5e01.halfstack
exercise_discussion_id: 99938
exercise_upload_id: 383276
modified_at: 24.4.2018
---

{% assign fullstack = "https://fullstackopen.github.io" %}

Ratkaise [Full stack open 2018]({{fullstack}}) materiaalin tehtävät

&nbsp; &nbsp; [(1.1) Vaihe 1: Jako komponenteiksi]({{fullstack}}/tehtävät#11-jako-komponenteiksi)   
&nbsp; &nbsp; [(1.2) Vaihe 2: Lisää komponentteja]({{fullstack}}/tehtävät#12-lisää-komponentteja)   
&nbsp; &nbsp; [(1.3) Vaihe 3: Tieto olioissa]({{fullstack}}/tehtävät#13-tieto-olioissa)   
&nbsp; &nbsp; [(1.4) Vaihe 4: Oliot taulukkoon]({{fullstack}}/tehtävät#14-oliot-taulukkoon)   
&nbsp; &nbsp; [(1.5) Vaihe 5: Yksi olio]({{fullstack}}/tehtävät#15)   

Tutustu materiaaliin siltä osin kuin se edeltää kohtaa [React-tehtävät, osa 1]({{fullstack}}/osa1#react-tehtävät-osa-1) ennen tehtävien *1.1* ja *1.2* ratkaisua, ja siltä osin kuin se edeltää kohtaa [Tehtäviä javascriptistä]({{fullstack}}/osa1#tehtäviä-javascriptistä) ennen tehtävien *1.3*, *1.4* ja *1.5* ratkaisua.

Ratkaisussa voi lähteä liikkeelle ladattavasta tehtäväpohjasta sen sijaan, että rakentaa sovelluksen rungon `create-react-app`ia käytäen. Pohjan saa toimintakuntoon lisäämällä siihen tarvittavat node-paketit komennolla `npm install`. Komento tulee antaa hakemistossa, jossa on riippuvuuden määrittelevä tiedosto `package.json`. Komennon antamisen myötä hakemistoon ilmestyy ilmestyy alihakemisto `node_modules`, joka koko sisältöineen on n. 200 MB.


Pohjan `index.js` on seuraavanlainen:

{% highlight js %}

import React from 'react';
import ReactDOM from 'react-dom';

import App from './App-0.js';
// import App from './todo/App-1.js';
// import App from './todo/App-2.js';
// import App from './todo/App-3.js';
// import App from './todo/App-4.js';
// import App from './todo/App-5.js';

ReactDOM.render(<App />, document.getElementById('root'));

{% endhighlight %}


Rakennettava `App`-komponentti laaditaan erilliseen tiedostoon, jonka päämoduuli ottaa käyttöönsä (`import App from ...`). Laadi lähteen *tehtävän 1.1* ratkaisu tiedostoon `App-1.js`, *tehtävän 1.2* ratkaisu tiedostoon `App-2.js` jne. Toteuta ratkaisut kumulatiivisesti siten, että esim. *tehtävän 1.2* ratkaisu sisältää myös *tehtävän 1.1* ratkaisun.

**Palauta** tehtävästä **yksi** tiedostoista `App-1.js`, `App-2.js`, `App-3.js`, `App-4.js` tai `App-5.js` riippuen siitä, mihin vaiheeseen asti ratkaisua olet vienyt.

Editoriksi materiaali ehdottaa [Visual Studio Codea](https://code.visualstudio.com/) tai [Atomia]( https://atom.io/), joista molemmat voi ladata veloituksetta. Tarvittavista työkaluista kerrotaan materiaalin kohdassa [Alkutoimet]({{fullstack}}/osa0#alkutoimet). *Git:iä* ei tarvita, koska ratkaisut palautetaan *Moodle:en*. *Chrome:n* ohella selaimena voi käyttää *Firefox:ia*.


