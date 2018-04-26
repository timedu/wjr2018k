---
layout: collection_index
permalink: /:collection/index.html
modified_at: 26.4.2018
---

[React][React] on osakseen [kasvavan suosion][score] saanut web-käyttöliittymien rakentamista tukeva JavaScript-kirjasto. 

Kurssin [Osan 2](../osa2) [Backbone][Backbone]-teeman yhteydessä oli esillä [Handlebars][Handlebars]-kirjasto. Käyttöliittymä rakennettiin lisäämällä html-merkkauksen oheen paikkoja dokumenttiin sisällytettävälle datalle sekä ns. *helpereitä*, joiden avulla esitettiin html:n ohessa esim. ehto- ja silmukkarakenteita. Osissa [3](../osa3) ja [4](../osa4) takasteltu [AngularJS][AngularJS] sisälsi oman [template][template]-tekniikkansa käyttöliittyminen rakentamiseen, missä html-merkkausta täydennettiin lisäattribuuteilla, ns. *direktiiveillä*, joilla voitiin esittää mm. ohjausrakenteita. *Handlebars* sisältää joukon valmiita *helpereitä* ja *AngularJS* valmiita *direktiivejä*, mutta kummassakin tapauksessa template-kieltä voidaan laajentaa laatimalla omia *helpereitä* tai *direktiivejä*.

Sekä *Handlebars*- että *AngularJS* -pohjaiset käyttöliittymät rakennetaan siten, että html-merkkausta täydennetään erityisillä lisäosilla esim. ohjausrakenteita varten. *React:in* yhteydessä toimitaan vastakkaisella tavalla niin, että JavaScript-koodiin oheen sisällytetään html-merkkausta muistuttavia rekenteita. Nämä rakenteet perustuvat [JSX][JSX]-kieleen, mikä sitten käänetään JavaScript:ksi. *React*-pohjainen sovellus muodostuu hierarkkisesti jäsentyvistä käyttöliittymäkomponenteista.


[React]: https://reactjs.org
[score]: https://hotframeworks.com/frameworks/react
[Backbone]: http://backbonejs.org
[Handlebars]: http://handlebarsjs.com
[AngularJS]: https://angularjs.org
[template]: https://docs.angularjs.org/guide/templates
[JSX]: https://facebook.github.io/jsx/


Lähdemateriaalina tässä käytetään Helsingin yliopistossa laaditun avoimen verkkokurssin [Full stack open 2018](http://mooc.fi/courses/2018/fullstack/) [aineistoa](https://fullstackopen.github.io/), jonka [sisällysluettelo]({{site.baseurl}}/fullstack) löytyy kootusti tältä sivustolta.



### Tehtävät

Tämän osan kaikki tehtävät on perustuvat [lähdemateriaaliin](https://fullstackopen.github.io/tehtävät/#osa-1). Poimitut 14 tehtävää on ryhmitehty kolmeksi tehtäväksi siten, että yksi lähteen tehtävä vastaa tässä yhtä tehtävän vaihetta. Tehtävien ratkaisut palautetaan edellisten osien tapaan Moodleen.

{% include exercises_list.md %}

[Tehtävä 5.1](tehtava51) sisältää viisi vaihetta. Lähtökohtana on yhdestä React-komponentista muodostuva "HalfStack"-opintojakson tietoja esittävä sovellus, joka jaetaan ensin kolmeksi komponentiksi ja  sitten yksi niistä vielä alikomponenteiksi. Kaikissa vaiheissa käyttöliittymä esittää datan samalla tavalla, mutta kolmessa viimeisessä vaiheessa lähtödatan jäsennys on erilainen. Tässä tehtävässä kaikki laadittavat komponentit ovat *funktionaalisia*. 

[Tehtävässä 5.2](tehtava52) rakennetaan UniCafe-ravintolalle palautteenkeruusovellus kuuden vaiheen kautta. *Ensimmäisen vaiheen* tuottamassa perusversiossa sovellus kerää painikkeiden avulla asiakasarvion (hyvä, neutraali, huono) ja esittää, kuinka monta asiakasta yhteensä on antanut kunkin arvio. Arviointidata talletetaan komponentin tilaan, joten tässä on käytettävä *luokkasyntaksiin perustuvaa* komponenttia. 

*Toisessa vaiheessa* sovellukseen lisätään laskentaa siten, että arvioista esitetään myös keskiarvo sekä positiivisten arvioiden osuus kaikista arvioista. *Vaiheessa 3* laadittu sovellus jäsennetään uudelleen niin, että se muodostuu luokkasyntaksiin perustuvan juurikomponentin lisäksi kolmesta funktionaalisesta komponentista. *Vaiheessa 4* sovellusta kehitetään edelleen siten, että statistiikka esitetään käyttöliittymässä vain, jos arvioita on annettu.

*Viides vaihe* muokkaa sovellusta niin, että kaikki painikkeet käyttävät samaa tapahtumakäsittelijää. Tämä edellyttää funktiota, jonka paluuarvona on funktio. *Viimeisessä vaiheessa* tehtävien muutosten myötä statistiikka esitetään käyttöliittymän muodostavalla sivulla html-taulukossa.

[Tehtävän 5.3](tehtava53) sovellus esittää ohjelmistotuotantoon liittyviä anekdootteja. *Ensimmäisen vaiheen* myötä sovelluksessa on painike, joka klikkaaminen tuo esiin anekdoottien joukosta satunnaisesti yhden. *Toisessa vaiheessa* sovellus kerää painikkeen avulla anekdoottien tykkäämisiä. *Viimeisessä vaiheessa* sovellus esittää aina myös toistaiseksi eniten tykätyn anekdootin. 

### Lisätietoja

[React Fundamentals](https://www.udacity.com/course/react-fundamentals--cx43) (Udacity)   
[Introduction to ReactJS](https://www.edx.org/course/introduction-to-reactjs) (edX)  
[ReactJS Tutorial](https://www.tutorialspoint.com/reactjs/index.htm) (TutorialsPoint)

