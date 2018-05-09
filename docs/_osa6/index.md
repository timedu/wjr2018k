---
layout: collection_index
permalink: /:collection/index.html
modified_at: 9.5.2018
---

Tässä osassa jatketaan [edellisen osan](../osa5) *React* -teemaa käyttäen ohjenuorana Helsingin [Full stack open 2018](https://fullstackopen.github.io/osa2/) -materiaalia. *Edellinen osa* tarkasteli React-kirjaston perusteita kuten funktiona ja luokkasyntaksilla määriteltäviä komponentteja, tietojenvälitystä komponentista toiseen, komponentin tilaa ja sen ylläpitoa sekä reagointia komponentteihin liittyviin tapahtumiin. *Tässä osassa* esillä olevia keskeisiä aiheita ovat mm.
JavaScriptin taulukkometodien käyttö käyttöliittymän muodostamisessa, komponenttien jako erillisiin tiedostoihin, html-lomakkeet sekä kommunikointi palvelimen kanssa. Kuten edellisessäkin osassa lähdemateriaali johdattelee aiheisiin kehittelemällä vaiheittain esimerkkinä toimivaa muistiinpano-sovellusta.


### Tehtävät

Myös tämän osan kaikki tehtävät on perustuvat [lähdemateriaaliin](https://fullstackopen.github.io/tehtävät/#osa-2). Lähteen 19 tehtävää on ryhmitehty kolmeksi tehtäväksi siten, että yksi lähteen tehtävä vastaa tässä yhtä tehtävän vaihetta. Tehtävien ratkaisut palautetaan edellisten osien tapaan Moodleen. Osan enimmäissuoritukseen riittää 15 tehtäväpistettä, minkä saavuttaminen ei edellytä aivan kaikkien vaiheiden ratkaisua.

{% include exercises_list.md %}


[Tehtävässä 6.1](tehtava61) palataan jo [edellisessä osassa](../osa5) esillä olleeseen kurssitietoja esittävään sovellukseen, jota tässä kehitetään hieman eteenpäin. Tarkoituksena on soveltaa erityisesti JavaScriptin taulukko-olion metodeja.
Tehtävä sisältää viisi vaihetta, joiden lähtökohdaksi voi ottaa [Tehtävän 5.1](../osa5/tehtava51) ratkaisun. 

[Tehtävässä 6.2](tehtava62) rakennetaan puhelinmuistio-sovellus ensin (vaiheet 1-5) siten, että nimet ja niihin liittyvät numerot talletetaan ainoastaan komponentin tilaan. Tässä tarkastelun kohteena on html-lomake sekä tiedonvälitys lomakkeen ja komponentin tilan välillä. Tämän jälkeen (vaiheet 6-10) sovellusta muokataan siten, että se käsittelee palvelinpäähän tallettuja numerotietoja ns. REST-rajapinnan kautta. Lopuksi (vaiheet 11-12) sovellusta vielä täydennetään käyttäjälle annettavilla eri toimintoihin liittyvillä palauteviesteillä ja samalla myös niin, että se huomio eräitä tietojen samanaikaisesta käsittelystä johtuvia poikkeustilanteita.

[Tehtävässä 6.3](tehtava63) rakennetaan kahdessa vaiheessa sovellus, joka esittää syötteenä annetun valtion pääkaupungin, asukasluvun sekä lipun. Sovellus perustuu valmiiseen verkosta löytyvään koneluettavaan REST-rajapintaan.
