---
layout: site_page
title: Tehtävien testeistä
---

Tehtäväpohjat sisältävät tyypillisesti joukon testitapauksia, joita ajetaan selaimessa avaamalla pohjassa oleva dokumentti `SpecRunner.html`.  Dokumentin viittaamat testitapaukset ovat hakemistossa `spec` sijaitsevissa JavaScript -tiedostoissa. Testit on toteutettu [Jasmine](http://jasmine.github.io/) -kirjastolla, joka otetaan käyttöön verkon yli[^1].

#### Testien onnistuminen ja epäonnistuminen

Jos SpecRunner tuo esiin sävyltään vihreän sivun, ovat testit menneet läpi. Sivulla on tällöin testitapausten luettelo, jonka otsikossa näkyy ajettujen testien kokonaismäärä ja epäonnistuneiden testien määränä on 0.

Jos ilmestyvällä sivulla on punaista, kaikki testit eivät ole onnistuneet. Sivu esittää nyt epäonnistuneet testit ja epäonnistumisten syyt[^2]. Testi epäonnistuu, jos testattava koodi aiheutaa poikkeustilanteen tai se antaan virheellisen tuloksen.

Esim. testi `Puhelinmuistion käyttö: ei alusta muistiota numeroilla`[^3] edellyttää, että metodi `annaNumerot` palauttaa tyhjän taulukon, kun kutsun parametrina annetaan nimi, jolle ei ole talletettu numeroja. Testin epäonnistuminen voi johtua esim. siitä, että koodista ei löydy ko. metodia, metodi palauttaa taulukon sijaan arvon null tai metodin palauttaman taulukon alkioiden lukumäärä on yksi. Näihin epäonnistumisiin liittyy seuraavanlaiset ilmoitukset:

* `TypeError: muistio.annaNumerot is not a function ...`
* `TypeError: muistio.annaNumerot(...) is null ...`
* `Expected 1 to equal 0.`

[^1]: Testien ajaminen edellyttää verkkoyhteyttä.
[^2]: Epäonnistumisen jälkeen on vielä epämääräisen näköistä tekstiä, joka esittää epäonnistuneen testin sijainnin ao. JavaScript-tiedostossa sekä testauskirjaston funktioiden kutsupolun.
[^3]: Voi olla, että joitakin testeita ei ole nimetty kovin osuvasti.

#### Osan 1 tehtävien "black box"-testitapaukset

Testit tutkivat ratkaisun rakennetta sekä suorittavat koodia vastaavalla tavalla kuin esimerkiksi sovelluspohjan mukana oleva käyttölittymä. Jälkimmäinen ryhmä, *Puhelinmuistion käyttö*,  sisältää kaikkien Osan 1 tehtävien osalta seuraavat 11 testiä:

* *Ei alusta muistiota numeroilla*: Metodi `annaNumerot` palauttaa tyhjän taulukon, kun kutsun parametrina annetaan nimi, jolle ei ole talletettu numeroja.

* *Lisää numeron henkilölle*: `lisaaNumero`-metodilla lisätty numero palautuu `annaNumero`-metodilla.

* *Ei lisää samaa numeroa kahteen kertaan*: useasti `lisaaNumero`-metodilla henkilölle lisätty sama numero palautuu `annaNumero`-metodilla ainoastaan yhteen kertaan.

* *Lisää henkilölle useita numeroita*: `annaNumero`-metodi palauttaa kaikki `lisaaNumero`-metodilla henkilölle lisätyt numerot.

* *Ei lisää henkilön numeroa toiselle henkilölle*: Henkilölle `lisaaNumero`-metodilla lisätty numero ei löydy toiselta henkilöltä `annaNumerot`-metodilla (jos tuota samaa numeroa ei ole lisätty toiselle henkilölle).

* *Lisää numeroita monelle henkilölle*:  Eri henkilöille `lisaaNumero`-metodilla lisätyt numerot palautuvat `annaNumerot`-metodilla.

* *Ei poista numeroa, jos hakuehto (nimi) ei toteudu*: Henkilölle (a) kaikki `lisaaNumero`-metodilla lisätyt numerot palautuvat `annaNumerot`-metodilla senkin jälkeen, kun toiselta henkilöltä (b) on pyritty poistamaan `poistaNumero`-metodilla henkilölle (a) lisättyä numeroa.

* *Ei poista numeroa, jos hakuehto (numero) ei toteudu*: Henkilölle kaikki `lisaaNumero`-metodilla lisätyt numerot palautuvat `annaNumerot`-metodilla senkin jälkeen, kun henkilöltä on pyritty poistamaan `poistaNumero`-metodilla numeroa, jota ei ole muistiossa.

* *Poistaa numeron toteutuvilla hakuehdoilla*: Muistosta `poistaNumero`-metodilla poistettu numero ei palaudu `annaNumerot`-metodilla.

* *Poistaa viimeisenkin numeron muistiosta*: `annaNumerot`-metodi palauttaa tyhjän taulukon sen jälkeen, kun `poistaNumerot`-metodilla on poistettu henkilön kaikki numerot.

* *Palauttaa luettelon, jonka kautta ei voi lisätä numeroa muistioon*: `annaNumerot`-metodin palauttamaan taulukkoon lisätty numero ei palaudu lisäyksen jälkeen toistetulla `annaNumerot`-metodin kutsulla.

<br/>

Alaviitteet
