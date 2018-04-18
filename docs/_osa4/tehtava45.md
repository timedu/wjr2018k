---
layout: exercise_page
title: "Tehtävä 4.5: Hello Firebase (2p)"
exercise_template_name: # W4E05.HelloFirebase
exercise_discussion_id: # 99284
exercise_upload_id: # 382325
modified_at: 16.4.2018
kesken: 1
julkaisu: 18.4.2018
no_review: 1
---

Hello Firebase

{% comment %}

Tämä on [seuraavaa tehtävää](../tehtava46) valmisteleva tehtävä, joka perustuu kurssilukemiston [Tehtävään 35]({{site.baseurl}}/weso/#vk-5-t35). Seuraavassa tehtäväkuvauksen lähtökohtana on lähteestä poimittu lainaus, jota on tässä hivenen muokattu.

> Rekisteröidy [Firebaseen][firebase] ja lisää sinne dataa, jonka sisältö on `{ message: 'Hello, World!' }` (`message`-kenttä, jonka arvo on `Hello, World!`).
>
> Muokkaa tehtäväpohjaa siten, että `app.js`-tiedostossa sijaitseva `Firebase`-palvelu hakee lisäämäsi datan Firebasesta. Muokkaa sen jälkeen saamassa tiedossa sijaitsevaa `HelloCtrl`-kontrolleria niin, että se käyttää `Firebase`-palvelua hakemaan Firebasesta viestin "Hello, World!" ja esittää sen näkymässä. Injektoi `Firebase`-palvelu kontrolleriin, jotta sen käyttäminen onnistuu.

[firebase]: https://firebase.google.com

Kurssilukemiston esimerkit ja tehtävät perustuvat Firebasen edelliseen versioon. Tässä kuitenkin käytetään Firebasen uudempaa versiota, jonka käyttö sekä web-konsolilla että sovelluksella on hieman erilaista.

Googlen Firebase löytyy osoitteesta <https://firebase.google.com>. Palvelua voi käyttää Google-tunnuksilla. Sen käyttö on veloituksetonta tiettyyn rajaan asti (ks. [Pricing][pricing]). Palveluun voi perustaa omia projekteja, joita hallinnoidaan [konsoli][console]-sovelluksen avulla.

[pricing]: https://firebase.google.com/pricing/
[console]: https://console.firebase.google.com

Tässä kehitetään selainpään sovellus, joka hyödyntää Firebase-palvelun tarjoamaa tietokantaa. Tätä varten luodaan[^1] konsolilla uusi Firebase-projekti (esim. *hello*). Projektin *Overview*-sivulta löytyy tieto, miten projekti kytketään selainsovellukseen (*"Add Firebase to your web app"*). AngulaJS:n Firebase-rajapintaa käytettäessä kytkemissä kannattanee hyödyntää ao. käsikirjan antamaa [ohjetta][initialize].

[initialize]: https://github.com/firebase/angularfire/blob/master/docs/reference.md#initialization

[^1]: Firebasen käyttö on sinun ja Googlen välinen kahdenkeskinen sopimus

Konsolin valikosta löytyvällä *Database* -valinnalla saa esiin sivun, jonka kautta voi ylläpitää projektin tietokannan tietoja. Tietokannan muotona on hierarkkisesti jäsentyvä avain-arvo -tyyppinen rakenne (vrt. JSON). Tämä tehtävä odottaa seuraavanlaista sisältöä tietokannalle:

~~~
hello-d4d6f
  |
  +- message: "Hello, World!"
~~~

Oletusarvoisesti tietokannan käyttö edellyttää käyttäjän autentikointia. Tässä voitanee kuitenkin sallia tietojen lukeminen ilman tunnistautumistta. Tietokannan käyttöön liittyviä sääntöjä voidaan kuvata sivun *RULES*-välilehdellä. Esim. seuraavat säännöt sallivat tietojen lukemisen ilman autentikointia, mutta tietojen muuttaminen edellyttää tunnistautumista:

~~~
{
  "rules": {
    ".read": true,
    ".write": "auth != null"
  }
}
~~~

Kun Firebase-konsolilla on suoritetta em. tehtävät voidaan ryhtyä kehittämään selainsovellusta. Tehtäväpohjassa on valmis näkymä, `index.html`.

{% highlight html %}
{% raw %}

    <body ng-app="HelloApp">

        <h3 ng-controller="HelloCtrl">
            Firebase says "{{data.message}}"
        </h3>

        <script src="todo/app.js"></script>

    </body>

{% endraw %}
{% endhighlight %}

Index-sivun viittaamassa tietossa `app.js` on runko, johon laaditaan tarvittava koodi: kytkeminen "pilvessä" olevaan Firebase-projektiin (`config`), sovelluksen Firebase-`service` sekä edellistä hyödyntävä HelloCtrl-`controller`.

**Palauta** tehtävästä tiedosto `app.js`. Varmista ennen palautusta, että sovellus toimii odotetusti. Jos pohjakoodi sisältää testejä, varmista myös niiden läpimeno ilman virheilmoituksia.

### Lisätietoja

Kun selainsovellus on kytkeytty Firebase-projektiin, viite sen tietokantaan saadaan seuraavasti[^2]:

[^2]: Firebasen aiemmassa versiossa käytäntö on hieman toisenlainen (vrt. kurssilukemisto).

~~~
var ref = firebase.database().ref();
~~~

Firebase-rajapintaa  käsitellään  kurssilukemiston[^3] luvuissa [13][weso-13] ja [17][weso-17]. Kattava esitys rajapinnasta löyttyy sen [käsikirjasta][angularfire].

[^3]: Huom. erilaiset käytännöt tietokantaviitteissä eri Firebase-versioiden välillä.

[weso-13]: {{site.baseurl}}/weso/#13-Jatketaan-keskustelua-palvelimen-kanssa:-Firebase
[weso-17]: {{site.baseurl}}/weso/#17-Suurempi-Angular-sovellus:-Elokuvakirjasto
[angularfire]: https://github.com/firebase/angularfire/blob/master/docs/reference.md





#### Alaviitteet

{% endcomment %}
