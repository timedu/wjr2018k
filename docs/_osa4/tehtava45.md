---
layout: exercise_page
title: "Tehtävä 4.5: Hello Firebase (2p)"
exercise_template_name: W4E05.HelloFirebase
exercise_discussion_id: 99284
exercise_upload_id: 382325
modified_at: 19.4.2018

---


Perusta [Firebaseen][firebase] -palveluun tietokanta ja lisää sinne seuraava data[^1]:


[^1]: `message`-kenttä, jonka arvo on `Hello, World!`.
[firebase]: https://firebase.google.com


{% highlight js %}

{ message: 'Hello, World!' }

{% endhighlight %}


Muokkaa sitten  tehtäväpohjan tiedostoa `HelloApp.js` siten, että sovellus esittää tietokantaan talletetun datan sivulla:

![UI](../img/hello-firebase.png "UI"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 1. </small>


**Palauta** tehtävästä tiedosto `HelloApp.js`, kun sovellus toimii odotetusti. 


### Lisätietoja

#### Tietokannan perustamisesta

Googlen Firebase löytyy osoitteesta <https://firebase.google.com>. Palvelua voi käyttää Google-tunnuksilla. Sen käyttö on veloituksetonta tiettyyn rajaan asti (ks. [Pricing][pricing]). Palveluun voi perustaa omia projekteja, joita hallinnoidaan [konsoli][console]-sovelluksen avulla.

[pricing]: https://firebase.google.com/pricing/
[console]: https://console.firebase.google.com

Tässä kehitetään selainpään sovellus, joka hyödyntää Firebase-palvelun tarjoamaa tietokantaa. Tätä varten luodaan[^2] konsolilla uusi Firebase-projekti (esim. *hello*). 

[^2]: Firebasen käyttö on sinun ja Googlen välinen kahdenkeskinen sopimus. Jos koet sen ongelmallisena, tämä tehtävä voidaan korvata jollakin toisella.

Konsolin valikosta löytyvällä *Database* -valinnalla saa esiin sivun, jonka kautta voi ylläpitää projektin tietokannan tietoja. Tässä otetaan käyttöön *Realtime Database*. Tietokannan muotona on hierarkkisesti jäsentyvä avain-arvo -tyyppinen rakenne (vrt. JSON). Tämä tehtävä odottaa seuraavanlaista sisältöä tietokannalle:

~~~
hello-d4d6f
  |
  +- message: "Hello, World!"
~~~

Tietokannan käyttöön liittyviä sääntöjä voidaan kuvata sivun tietokannan *RULES*-välilehdellä. Esim. seuraavat säännöt sallivat tietojen lukemisen mutta ei kirjoittamista:

~~~
{
  "rules": {
    ".read": true,
    ".write": false
  }
}
~~~

#### Sovelluksen rakentamisesta

Tämä tehtävä ratkennee AngularFire-rajapinnan [Quickstart][quickstart]-ohjeen perusteella. Kannattanee silmäillä erityisesti kohdissa 3 ja 4 olevia esimerkkejä. Tarkoitus on, että initialisointiin liittyvä koodi laaditaan pohjan "config"-funktioon.

[quickstart]: https://github.com/firebase/angularfire/blob/master/docs/quickstart.md

Tarvittavat tunnisteet löytyvät Firebase-konsolista. Projektin *Overview*-sivulta löytyy tieto, miten projekti kytketään selainsovellukseen (*"Add Firebase to your web app"*).

#### Lähteitä

Tämä tehtävän lähtökohtana on Web-selainohjelmointi -aineiston 
[Tehtävä 35](http://web-selainohjelmointi.github.io/#vk-5-t35). 
Firebase-rajapintaa  käsitellään  lukemiston luvuissa [13][weso-13] ja [17][weso-17]. 
Aineiston esimerkit ja tehtävät perustuvat kuitenkin Firebasen vanhempaan versioon, jonka käyttö sekä web-konsolilla että sovelluksella on hieman erilaista.

Kattava esitys AngularFire-rajapinnasta löytyy sen [käsikirjasta][angularfire].

[weso-13]: http://web-selainohjelmointi.github.io/#13-Jatketaan-keskustelua-palvelimen-kanssa:-Firebase

[weso-17]: http://web-selainohjelmointi.github.io/#17-Suurempi-Angular-sovellus:-Elokuvakirjasto

[angularfire]: https://github.com/firebase/angularfire/blob/master/docs/reference.md


<br/>


