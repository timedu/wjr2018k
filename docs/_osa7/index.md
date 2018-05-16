---
layout: collection_index
permalink: /:collection/index.html
modified_at: 16.5.2018
---


Kurssin viimeisessä osassa on esillä *backendin* rakentaminen *React*-pohjaisen sovelluksen (*frontendin*) taakse, mitä käsitellään lähteenä toimivan Helsingin *Full stack open 2018* -materiaalin [kolmannessa osassa](https://fullstackopen.github.io/osa3/). Palvelinpään teknologiapohjana  toimii [Node][Node] -JavaScript runtime, [Express][Express] -sovelluskehys sekä [MongoDB][MongoDB] -dokumenttitietokanta, jota käytetään [mLab][mLab] -pilvipalvelun kautta. Tietokantarajapintana on [mongoose][mongoose], jonka kautta kannassa oleva tietokokonaisuus (kokoelma) näkyy sovelluksessa JavaScript -objektina. 


[Node]: https://nodejs.org/en/
[Express]: https://expressjs.com
[MongoDB]: https://www.mongodb.com
[mLab]: https://mlab.com
[mongoose]: http://mongoosejs.com



### Tehtävät

Lähteen [kolmanteen osaan](https://fullstackopen.github.io/osa3/) sisältyy yhteensä 22 [tehtävää](https://fullstackopen.github.io/tehtävät/#osa-3), joista tähän on poimittu 17 siten, että ne on ryhmiteltynä yhteensä neljäksi tehtäväksi. Osan enimmäissuoritukseen riittää 15 tehtäväpistettä, minkä saavuttaminen ei edellytä aivan kaikkien tehtäviin sisältyvien vaiheiden ratkaisua.

{% include exercises_list.md %}

[Tehtävässä 7.1](tehtava71) rakennetaan puhelinluettelo-sovellukseen REST-rajapinnan tarjoava *backend*, jonka kautta voidaan kysellä ja ylläpitää numerotietoja. Ratkaisussa hyödynnettään valmista moduulia, joka esittää konsolille tietoja rajapintaan tulevista pyynnöistä. 
[Tehtävässä 7.2](tehtava72) edellä rakennettu *backend* sovitetaan toimimaan yhdessä [Tehtävässä 6.2](../osa6/tehtava62) laaditun *frontendin* kanssa. [Tehtävässä 7.3](tehtava73) perustetaan pilvipalveluun tietokanta ja kokeillaan sen käyttöä komentorivipohjaisen sovelluksen avulla. [Tehtävässä 7.4](tehtava74) muokataan puhelinluettelo-sovelluksen *backend* käyttämään edellä perustettua tietokantaa.

