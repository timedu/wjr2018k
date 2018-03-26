---
layout: collection_index
permalink: /:collection/index.html
modified_at: 23.3.2018
---

[Backbone-kirjaston](http://backbonejs.org) avulla selainpäässä ajettavalle sovellukselle voidaan muodostaa [MVC][MVC]-tyyppisiä rakenteita. Soveluksen keskeisiä rakenneosia ovat *näkymät* (view), *mallit* (model) ja *kokoelmat* (collection). *Näkymä* on linkki käyttöliittymänä toimivan dokumentin ja muun sovelluksen välillä. Sen tehtävä on reagoida dokumentin tapahtumiin, esim. painikkeiden klikkauksiin, sekä lukea ja muokata selaimessa olevaa dokumentia. *Malli* ylläpitää joukkoa avain-arvo -pareja. Se voi mm. kelpoistaa tiedot ennen tietojen tallettamista malliin. *Kokoelma* taas edustaa mallien joukkoa. Sen voi kytkeä suoraan [REST][REST]-rajapinnan toteuttavaan web-palveluun, jolloin tietojen välitys kokoelman ja palvelun välillä toimii saumattomasti - esim. uuden mallin lisääminen kokoelmaan aikaansaa sen, että mallin sisältämät tiedot välittyvät automaattisesti web-palveluun. *Näkymän* voi asettaa seuraamaan mallin ja kokoelman tietosisällössä tapahtuvia muutoksia, joihin malli voi reagoida esim. esittämällä muuttuneet tiedot selaimessa olevassa dokumentissa.

[MVC]: https://en.wikipedia.org/wiki/Model–view–controller
[REST]: https://en.wikipedia.org/wiki/Representational_state_transfer

### Tehtävät

Kurssin tämän osan tehtävät ovat modifikaatioita Helsingin yliopiston Web-selainohjelmointi -kurssin erään toteutuksen aineistosta[^1]. Siten tehtävien pohjaksi kannattanee lukaista ainestosta [Backbone-kirjastoa käsittelevä poiminta](weso-backbone).

[^1]: <small>Materiaali tehtävineen on lisensoitu Creative Commons BY-NC-SA-lisenssillä. Alkuperäisen materiaalin kirjoittaja on *Arto Vihavainen* ja sen syntyyn ovat vaikuttaneet useat tahot, joista tärkeimmäksi on mainittu *Mikael Nousiainen*. Myös nimi *Kasper Hirvikoski* tuodaan esiin.</small>

{% include exercises_list.md %}

Neljässä ensimmäisessä tehtävässä toteutetaan yksinkertainen laskuri hieman erilaisin periaattein. [Tehtävässä 2.1](tehtava21) muodostetaan Backbone-näkymä, joka reagoi käyttöliitymässä olevan painikkeen klikkauksiin muuttamalla ylläpitämänsä laskurin arvoa ja esittämällä muuttuneen arvon käyttöliittymässä. [Tehtävässä 2.2](tehtava22) käyttöliittymän muutokset toteutetaan [Handlebars][Handlebars]-templaten avulla. [Tehtävän 2.3a](tehtava23a) ratkaisu perustuu kahteen näkymään, joista toinen reagoi käyttöliittymän painikkeen klikkauksiin ja toinen ylläpitää laskurin arvoa ja esittää sen käyttöliittymässä. Kommunikointi näkymien välillä toteutetaan itse määritellyn tapahtuman avulla. [Tehtävässä 2.3b](tehtava23b) on kahden näkymän lisäksi laskurin arvoa ylläpitävä malli. Toinen näkymistä reagoi painikkeen klikkaukseen muuttamalla mallia. Toinen näkymä seuraa mallissa tapahtuvia muutoksia, ja niiden seurauksena lukee mallista laskurin arvon ja esittää sen käyttöliittymässä.

[Handlebars]: http://handlebarsjs.com

Seuraavat kaksi tehtävää ovat keskenään samarakenteisia. Molemmissa on *malli* ja *näkymä*, ja käyttöliittymän päivitys tapahtuu *templaten* avulla. Molempien sovellusten näkymät myös reagoivat käyttöliittymän klikkauksiin. [Tehtävässä 2.4](tehtava24) sivulla esitetään henkilön tietoja siten, että sivun klikkaus aiheuttaa henkilö iän kasvamisen. [Tehtävässä 2.5](tehtava25) on kello, jonka tikitys käynnistyy ja pysähtyy sitä klikkaamalla. Jälkimmäisen tehtävän kuvaus ottaa edelliseen verrattuna jokin verran enemmän kantaa ratkaisun toteutusperiaatteeseen.

[Tehtävässä 2.6](tehtava26) rakennettava unipäiväkirja -sovellus on aiempiin tehtäviin nähden hieman laajempi. Käyttäjän näkökulmasta sovellus muodostuu useasta sivusta vaikka se teknisesti on vain yksisivuinen. Sovellus muodostuu neljästä *näkymästä* ja yhdestä *malleja* sisältävästä *kokoelmasta*.  Näkymistä kolme käyttää *templatea* käyttöliittymän muokkaamiseen. Näkymät kommunikoivat keskenään *tehtävän 2.3a* tapaan itse määriteltyjen tapahtumien avulla.

Tehtävissä 2.7 ja 2.8 rakennetaan käyttäjän kannalta samanlaiset tehtävälista-sovellukset, joilla käyttäjä voi lisätä listaan uusia tehtäviä sekä muuttaa listassa olevien tehtävien statusta. [Tehtävässä 2.7](tehtava27) lista talletetaan ainoastaan *kokoelmaan*, mutta [Tehtävässä 2.8](tehtava28) tiedot välittyvät kokoelman kautta web-palvelulle.



### Lisätietoja

[Developing Backbone.js Applications](https://addyosmani.com/backbone-fundamentals/) by *Addy Osmani*   
[Learn Backbone.js](https://eu.udacity.com/course/learn-backbonejs--ud990) by *Udacity*   
[Backbone, the Primer](https://github.com/jashkenas/backbone/wiki/Backbone%2C-The-Primer)   

<br/>
