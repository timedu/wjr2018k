---
layout: collection_index
permalink: /:collection/index.html
kesken: 1
modified_at: 25.4.2018
julkaisu: vielä täydennettynä 26.4.2018
---

> [React](https://reactjs.org) is a front-end library developed by Facebook. It is used for handling the view layer for web and mobile apps. ReactJS allows us to create reusable UI components. It is currently one of the most popular JavaScript libraries and has a strong foundation and large community behind it.  
[ [ReactJS Tutorial](https://www.tutorialspoint.com/reactjs/index.htm) ]

Lähdemateriaali: [Full stack open 2018](https://fullstackopen.github.io/)
([sisällysluettelo]({{site.baseurl}}/fullstack))


### Tehtävät

Tämän osan kaikki tehtävät on perustuvat lähdemateriaaliin. Poimitut 14 tehtävää on ryhmitehty kolmeksi tehtäväksi siten, että yksi lähteen tehtävä vastaa tässä yhtä tehtävän vaihetta. 

{% include exercises_list.md %}

[Tehtävä 5.1](tehtava51) sisältää viisi vaihetta. Lähtökohtana on yhdestä React-komponentista muodostuva "HalfStack"-opintojakson tietoja esittävä sovellus, joka jaetaan ensin kolmeksi komponentiksi ja  sitten yksi niistä vielä alikomponenteiksi. Kaikissa vaiheissa käyttöliittymä esittää datan samalla tavalla, mutta kolmessa viimeisessä vaiheessa lähtödatan jäsennys on erilainen. Tässä tehtävässä kaikki laadittavat komponentit ovat *funktionaalisia*. 

[Tehtävässä 5.2](tehtava52) rakennetaan UniCafe-ravintolalle palautteenkeruusovellus kuuden vaiheen kautta. *Ensimmäisen vaiheen* tuottamassa perusversiossa sovellus kerää painikkeiden avulla asiakasarvion (hyvä, neutraali, huono) ja esittää, kuinka monta asiakasta yhteensä on antanut kunkin arvio. Arviointidata talletetaan komponentin tilaan, joten tässä on käytettävä *luokkasyntaksiin perustuvaa* komponenttia. 

*Toisessa vaiheessa* sovellukseen lisätään laskentaa siten, että arvioista esitetään myös keskiarvo sekä positiivisten arvioiden osuus kaikista arvioista. *Vaiheessa 3* laadittu sovellus jäsennetään uudelleen niin, että se muodostuu luokkasyntaksiin perustuvan juurikomponentin lisäksi kolmesta funktionaalisesta komponentista. *Vaiheessa 4* sovellusta kehitetään edelleen siten, että statistiikka esitetään käyttöliittymässä vain, jos arvioita on annettu.

*Viides vaihe* muokkaa sovellusta niin, että kaikki painikkeet käyttävät samaa tapahtumakäsittelijää. Tämä edellyttää funktiota, jonka paluuarvona on funktio. *Viimeisessä vaiheessa* tehtävien muutosten myötä statistiikka esitetään käyttöliittymän muodostavalla sivulla html-taulukossa.

[Tehtävän 5.3](tehtava53) sovellus esittää ohjelmistotuotantoon liittyviä anekdootteja. *Ensimmäisen vaiheen* myötä sovelluksessa on painike, joka klikkaaminen tuo esiin anekdoottien joukosta satunnaisesti yhden. *Toisessa vaiheessa* sovellus kerää painikkeen avulla anekdoottien tykkäämisiä. *Viimeisessä vaiheessa* sovellus esittää aina myös toistaiseksi eniten tykätyn anekdootin. 

### Lisätietoja

* <https://www.udacity.com/course/react-fundamentals--cx43>
* <https://www.edx.org/course/introduction-to-reactjs>
* <https://www.tutorialspoint.com/reactjs/index.htm>
* <https://facebook.github.io/jsx/>
