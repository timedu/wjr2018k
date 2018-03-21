---
layout: exercise_page
title: "Tehtävä 2.6: Sleepy (3p)"
exercise_template_name: W2E06.Sleepy
exercise_discussion_id: 97785
exercise_upload_id: 380365
modified_at: 21.3.2018
---

Tehtävässä on toteutettavana unipäiväkirja, jossa on kaksi toimintoa: *unen lisääminen* ja *unistatistiikan listaaminen*. Jokaisesta nukkumisesta kerätään *alkuaika*, *loppuaika, ja *freesiys (1-5)*. Sovelluksen latauduttua, selain esittää seuraavanlaisen sivun:

![Sleepy UI](../img/w2e06-sleepy-1.png "Sleepy UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 1.</small>

Esillä olevat elementit liittyvät näkymään, joka on tuotettu tehtäväpohjassa valmiina olevalla muodostinfunktiolla `NavigationView`. Kun *kuvan 1* esittämältä sivulta valitsee vaihtoehdon *Add entry*, esiin tulee seuraavanlainen sivu:

![Sleepy UI](../img/w2e06-sleepy-2.png "Sleepy UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 2.</small>

Sivulla olevalle lomakkeelle voi kirjata nukkumiskertaan liittyvät tiedot. Sovelluksen tulee tarkistaa, että freesiys-kenttään asetetaan numero, joka on väliltä 1-5[^1]. Lomake liittyy näkymään, joka on tuotettu tässä laadittavalla muodostinfunktiolla `AddEntryView`.

[^1]: Syötteen kelpoistaminen toteutetaan Backbone-mallin avulla.

Kun unipäiväkirjaan lisätään tietue, käyttäjälle näytetään viesti "Thx!" seuraavasti:

![Sleepy UI](../img/w2e06-sleepy-3.png "Sleepy UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 3.</small>

Palauteviesti liittyy näkymään, joka on tuotettu pohjassa valmiina olevalla muodostimella `FeedbackView`. Jos freesiys-kenttään on syötetty epäkelpo arvo, palauteviesti on seuraavanlainen:

![Sleepy UI](../img/w2e06-sleepy-4.png "Sleepy UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 4.</small>

Mallin suorittaman validoinnin seurauksena syntyneeseen virhetilanteeseen liittyvä viesti löytyy mallin `validationError`-ominasuudesta.

Kun käyttäjä valitsee sivulta vaihtoehdon *Statistics*, näytetään sivu, joka listaa tietueet. Näkymän lopussa tulostetaan freesiys-arvo, joka on keskiarvo kaikkien tietueiden sisältämistä arvoista:

![Sleepy UI](../img/w2e06-sleepy-5.png "Sleepy UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kuva 5.</small>

*Kuvan 5* tuloste liittyy näkymään, joka on tuotettu tässä laadittavalla muodostimella `StatisticsView`.

Toteuta vaihtoehtojen (*Add entry*, *Statistics*) valinta tapahtumien avulla seuraavasti (vrt. [Tehtävä 2.3a](../tehtava23a)):

![Diagram 1](../img/w2e06-diagram-1.png "Diagram 1"){: style="display: block; margin: auto; margin-top: 10px; width: 600px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kaavio 1.</small>

Myös palauteviestien esittämisessä tulee tukeutua tapahtumiin:

![Diagram 2](../img/w2e06-diagram-2.png "Diagram 2"){: style="display: block; margin: auto; margin-top: 10px; width: 600px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kaavio 2.</small>

Tiedot talletetaan [Backbone-kokoelmaan][collectiom], joka on luotu tässä laadittavalla muodostimella `EntryCollection`. Kokoelma näkyy ao. näkymissä muuttujassa `this.collection`. Kokoelman `model`-ominaisuuteen tulee määritellä "freesiys"-arvon validoinnin suorittava malli. Kokoelmalla tulee olla myös metodi `avgFreshness`, joka palauttaa kokoelmaan talletettujen freesiys-arvojen keskiarvon.

[collectiom]: http://backbonejs.org/#Collection

![Diagram 3](../img/w2e06-diagram-3.png "Diagram 3"){: style="display: block; margin: auto; margin-top: 10px; width: 600px; padding: 5px; border: thin solid lightgray; border-radius: 5px;"}

<small>Kaavio 3.</small>

**Palauta** tehtävän ratkaisuna tiedostot `AddEntryView.js`, `StatisticsView.js` ja `EntryCollection.js`.

<br/>
