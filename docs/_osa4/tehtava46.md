---
layout: exercise_page
title: "Tehtävä 4.6: Puhelinmuistio: Firebase"
exercise_template_name: # W4E06.PuhFirebase
exercise_discussion_id: # 99285
exercise_upload_id: # 382326
modified_at: 16.4.2018
kesken: 1
julkaisu: 18.4.2018
no_review: 1
---

Puhelinmuistio: Firebase

{% comment %}

Laadi puhelinmuistiosovellus, joka on ulkoiselta käyttäytymiseltään pääosin [tehtävän 4.4](../tehtava44) ratkaisun kaltainen. Laadittava sovellus kuitenkin tukeutuu tietojen talletuksen osalta [Firebase-tietokantaan][firebase-db]. Sovelluksen käyttö myös edellyttää käyttäjältään tunnistautumista, mikä toteteutetaan [Firebasen autentikointipalvelulla][firebase-auth].

[firebase-db]: https://firebase.google.com/docs/database/
[firebase-auth]: https://firebase.google.com/docs/auth/

### Käyttöliittymä

Sovelluksen ulkoasu ja reititys on pääosin kuten [tehtävässä 4.4](../tehtava44). Tunnistautumisvaatimus kuitenkin tuo näihin pieniä muutoksia.

![ui-1](../img/w4e06-1.png "ui-1"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 1. Hae numeroita -sivu (ei kirjauduttu).</small>

Jos käyttäjä ei ole tunnistautunut, *Hae numeroita* -sivulla on *Login* -painike. Tällöin *Nimi* -kenttään ei voi kirjoittaa ja *uusi numero* -linkki ei ole näkyvissä (Kuva 1).

Käyttäjä tunnistautuu klikkaamalla *Login* -painiketta. Jos tunnistautuminen onnistuu, näkymään ilmestyy *Login* -painikkeen tilalle *Logout* -painike, *Nimi* -kenttä aktivoituu ja *uusi numero* -linkki tulee näkyviin (Kuva 2).

*Logout* -painikkeen klikkaus palauttaa näkymän Kuvassa 1 esitetyn kaltaiseksi.

![ui-2](../img/w4e06-2.png "ui-2"){: style="display: block; margin: auto; margin-top: 10px; width: 400px;"}

<small>Kuva 2. Hae numeroita -sivu (kirjauduttu).</small>

#### Reititys

Kun käyttäjä on kirjautunut, sovelluksen näkymiin voidaan siirtyä painikkeiden ja linkkien ohella myös suorilla osoitteilla (vrt. [Tehtävä 4.4](../tehtava44)). Jos kirjautumista ei ole tehty, on suoralla osoitteella pääsy ainoastaan sovelluksen juuriosoitteeseen (`/W4E06/#/` tai `/W4E06/`), joka tuo esiin *Hae numeroita* -näkymän. Yritys muuhun osoitteeseen (esim. `/W4E06/#/bart`, `/W4E06/#/bart/remove/111` tai `/W4E06/#/jotakin/muuta`) palauttaa käsittelyn juuriosoitteeseen.


### Tietokanta

[Firebase-tietokanta][firebase-db] on avain-arvo -tyyppinen, missä arvo voi muodostua  avain-arvo -pareista. Tietokantaan ei voi sellaisenaan tallettaa taulukko -tyyppistä tietoa eikä tietävästi ole [kovin suositeltavaa][array-practices] käyttää nollasta lähteviä juoksevia numeerisia avaimia.

[array-practices]: https://firebase.googleblog.com/2014/04/best-practices-arrays-in-firebase.html

Edellisissä puhelinmuistio-toteutuksissa tiedot on talletettu sovelluksessa seuraavanlaiseen rakenteeseen:

{% highlight json %}

{ "bart": ["111", "222", "333"],
  "ned":  ["444", "555"] }

{% endhighlight %}

<small>Listaus 1. Tietojen rakenne edellisissä puhelinmuistio-toteutuksissa.</small>

Tässä edellä esitetyt taulukot tulisi muuntaan toisenlaiseksi rakenteeksi, joka voisi olla esim. seuraava:

{% highlight json %}

{
  "bart": {
    "_111": "111", 
    "_222": "222", "_333": "333" },
  "ned":  {"_444": "444", "_555": "555" } }

{% endhighlight %}

<small>Listaus 2. Taulukot muunnettu avain-arvo -rakenteeksi.</small>

Tällaisessa tilanteessa avaimet ja arvot voisivat olla samoja, mutta esim. *Listauksen 2*  esittämää periaatetta noudattaen sovellusta kehitettäessä ilmenee, onko kulloinkin käsittelyssä arvo vai sen avain.

Firebase-konsolissa *Listauksen 2* data näkyy seuraavasti:

~~~
puhelinmuistio-5e3d9
  |
  +-bart
  |   |
  |   +-_111: "111"
  |   |
  |   +-_222: "222"
  |   |     
  |   +-_333: "333"  
  |
  +-ned
      |
      +-_444: "444"
      |
      +-_555: "555"
~~~

<small>Kuva 3. Avain-arvo -rakenne Firebase -konsolissa.</small>

### Autentikointi

Firebase-projektin autentikonti-asetuksiin liittyvä sivu tulee esiin konsolin valikon *Authentication* -valinnalla. *SIGN-IN METHOD* -välilehdellä voi valita projektissa käytettävät tunnistusmenetelmät. Tässä käytetään *Email/Password* -tunnistusta.  Tunnistetiedot voi määritellä *USERS* -välilehdellä. *Email* -arvon ei tarvitse tässä olla oikea sähköpostiosoite.

Tietokantaan liittyvät tunnistautumissäännöt määritellään Firebase -konsolin *Database* -sivun *RULES* -välilehdellä. Oletuksena nämä säännöt ovat seuraavanlaiset:

{% highlight json %}

{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}

{% endhighlight %}

<small>Listaus 3. Firebase -tietokannan autentikointisääntöjen oletusarvot.</small>

Oletussäännöillä tietojen sekä lukeminen että kirjoittaminen edellyttää tunnistautumista. Tässä kannattaa pitäytyä oletusarvoissa.

### Sovelluksen rakenne

*Listauksessa 4* on pääsivun (`index.html`) `body`-elementin merkkaus.


{% highlight html %}

    <body ng-app="PuhApp">

        <h1>Puhelinmuistio</h1>

        <div ng-view></div>

        <script src="js/app.js"></script>

        <script src="js/firebase.auth.service.js"></script>
        <script src="js/button.directive.js"></script>             
        <script src="js/add.remove.controller.js"></script>

        <script src="todo/route.config.js"></script>
        <script src="todo/firebase.db.service.js"></script>
        <script src="todo/search.controller.js"></script>

    </body>

{% endhighlight %}

<small>Listaus 4. Sovelluksen pääsivun *body* -elementin merkkaus.</small>

Sovellukseen liittyy  seitsemän[^lisaksi-kirjastot] JavaScript -tiedostoa, joista kolme (`todo` -kansiossa olevat) palautetaan osana tehtävän ratkaisua. Suuri osa tarvittavasta koodista on tehtäväpohjassa tai kopioitavissa [tehtavän 4.4](../tehtava44) ratkaisusta (ks. [seuraava kohta](#ratkaisun-laatimisen-esimerkkivaiheistus)).

[^lisaksi-kirjastot]: Verkon yli ladattavien kirjastojen lisäksi

Pääsivun lisäksi sovellus sisältää kolme html-tiedostoa, joissa sijaitsevat sovelluksen näkymät (*Kuva 4*).

~~~
Site Root
  |
  +- todo
  |   |
  |   +- search.view.html
  |
  +- view
      |
      +- add.html
      |
      +- remove.html
~~~

<small>Kuva 4. Näkymät projektin hakemistopuussa.</small>

Näkymistä kaksi on tehtäväpohjassa. `todo` -kansiossa oleva `search.view.html` palautetaan täydennettynä osana tehtävän ratkaisua.


### Ratkaisun laatimisen esimerkkivaiheistus

#### *Lähtökohta*

Kun tehtäväpohjan käynnistää, selaimen ikkunaan ilmestyy sivu, joka sisältää sovelluksen pääotsikon *Puhelinmuistio*. Selaimen konsolille tulee ilmoitus "*Error: No Firebase App '[DEFAULT]' has been created - call Firebase App.initializeApp()*".

#### 1. Sovelluksen kytkentä Firebase -projektiin.

Kirjaa Firebase -projektisi tunnisteet ao. kohtaan tiedostossa `app.js`.

Tämän jälkeen em. virheilmoitusta ei enää pitäsi tulla selaimen konsolille. Tosin konsolille ilmestynee teksti "*User signed out.*", jonka tuottaa pohjassa valmiina oleva autentikaatioon liittyvä koodi.

#### *Vaihe I*

Askelten 2-5 toteuttamisen jälkeen sovelluksen pitäisi toimia [tehtävän 4.4](../tehtava44) kuvauksen mukaisesti.


#### 2. Näkymien reititys

Kopio [tehtävän 4.4](../tehtava44) ratkaisusta tiedoston `config.js` sisältö tiedostoon `route.config.js` ja tee kopioimaasi koodiin seuraavat *Hae numeroita* -näkymää koskevat muutokset:

{% highlight javascript %}

// ...

    // controller: 'PuhController',
    // templateUrl: 'view/search.html'
    controller:  'SearchController',
    templateUrl: 'todo/search.view.html'

// ...

{% endhighlight %}

Sovelluksen käynnistyessä *Hae numeroita* -näkymän pitäisi tulla nyt esiin. *Lisää numero* -näkymään pääsee kirjaamalla jotakin sivulla olevaan *Nimi* -kenttään ja klikkaamalla sitten *uusi numero* -linkkiä. Näkymiin pääsee myös suorilla osoitteilla, esim.  `/W4E06/#/` , `/W4E06/#/joku`, `/W4E06/#/joku/add` ja `W4E06/#/joku/remove/123`. *Lisää numero*- ja *Poistetaanko numero?* -näkymät eivät sisällä painikkeita.

#### 3. Ylläpito -näkymien painikkeet

Kopio [tehtävän 4.4](../tehtava44) ratkaisusta tiedoston `directive.js` sisältö tiedostoon `button.directive.js`.

 *Lisää numero*- näkymä sisältää nyt *Lisää*- ja *Peruuta* -painikkeet ja *Poistetaanko numero?* -näkymä sisältää *Poista*- ja *Peruuta* -painikkeet. Näkymissä olevien painikkeiden klikkaukset eivät vaihda esillä olevaa näkymää.

#### 4. Ylläpito -näkymien painikkeiden aktivointi

Kopio [tehtävän 4.4](../tehtava44) ratkaisun tiedostosta `controller.js` kontrollerien  sisältö tiedostoihin `add.remove.controller.js` (`AddController` ja `RemoveController`) ja `search.controller.js` (`SearchController`[^puh-controller]).

[^puh-controller]: Tehtävässä 4.4 vastinkontrolleri on nimeltään `PuhController`.

 *Lisää numero*- ja *Poistetaanko numero?* -näkymissä olevien painikkeiden klikkauksen pitäisi nyt tuoda esiin *Hae numeroita*- näkymän.

#### 5. Datan talletus sovellukseen

Kopio [tehtävän 4.4](../tehtava44) ratkaisusta tiedoston `service.js` metodien sisältö tiedoston `firebase.db.service.js` vastimetodeihin. Lisää palveluun myös kopioitujen metodien viitaama muuttuja:

{% highlight javascript %}
    var henkilot = {};
{% endhighlight %}

Sovelluksen pitäisi nyt toimia [tehtävän 4.4](../tehtava44) kuvauksen mukaisesti.

#### *Vaihe II*

Askelten 6-10 kautta voidaan ottaa käyttöön Firebase-tietokanta ja tunnistautuminen Firebasen avulla.

#### 6. Tunnistautuminen

Määrittele Firebase -projektiisi tunnistautumistiedot (ks. edellä [Autentikointi](#autentikointi)) ja kirjaa nämä tiedoston `app.js` määrittelemän vakion `FIREBASE_USER` arvoksi.

Varmista, että näkymän `search.view.html` *Login*- ja *Logout* -painikkeille on asettettu tapahtumakäsittelijät siten, että sisään- ja uloskirjautumisen voi suorittaa näiden painikkeiden avulla.

Nyt, klikattaessa *Login/Logout* painikkeita, selaimen konsolille pitäisi ilmestyä teksti "*User signed in*" tai "*User signed out*".


*Lisätietoja*: Tehtäväpohjan tiedostossa `firebase.auth.service.js` on palvelu `Auth`, joka määrittelee tässä tarvittavat tunnistautumiseen liittyvät funktiot. Vakio `FIREBASE_USER` injektoidaan `Auth`-palveluun. Tiedostossa `app.js` tunnistautumisfunktioita on asetettu sovelluksen globaaliin näkyvyysalueeseen[^root-scope] (`$rootScope`). Samassa yhteydessä on määritelty tapahtumakäsittelijä, joka mm. tulostaa selaimen konsolille tekstin "*User signed in*" tai "*User signed out*" kirjautumisen tian vaihtuessa.

[^root-scope]: Näkymä voi viitata globaalin näkyvyysalueen (`$rootScope`) tunnisteisiin samoin kuin sen kontrollerikohtaisen näkyvyysalueen (`$scope`) tunnisteisiin.

#### 7. Tunnistautumisen huomiointi näkymässä

Muokkaa näkymää `search.view.html` siten, että sen ulkoasu riippuu kirjautumisen tilasta edellä kohdassa [Käyttöliittymä](#kyttliittym) esitetyllä tavalla.

*Vihjeitä*: Esim. direktiiveistä [ng-disabled][ng-disabled], [ng-hide][ng-hide] ja  [ng-show][ng-show] saattaa olla tässä hyötyä. Tehtäväpohjasta löytynee sovelluksen yleisen näkyvyysalueen (`$rootScope`) muuttuja, jota voidaan hyödyntää tämän ominaisuuden toteutuksessa.

[ng-disabled]: https://docs.angularjs.org/api/ng/directive/ngDisabled
[ng-hide]: https://docs.angularjs.org/api/ng/directive/ngHide
[ng-show]: https://docs.angularjs.org/api/ng/directive/ngShow

#### 8. Tunnistautumisen huomiointi reitityksessä

Muokkaa reitityskonfiguraatiota `route.config.js` siten, että pääsy sovelluksen osoitteisiin riippuu kirjautumisen tilasta edellä kohdassa [Reititys](#reititys) kuvatulla tavalla.

Muokkauksen jälkeen, pyrittäessä osoitteeseen, johon pääsy ei ole sallittu ilman kirjautumista, selaimen konsolille tulostuu teksti "*AUTH_REQUIRED*", ja selaimeen ilmestyy *Hae numeroita* -näkymä.

*Vihjeitä*: Asiaa käsitellään kurssilukemiston [kohdassa 17.5][kohta-17.5]. Tässä riittänee reitityskonfiguraatiotiedoston päivitys. Tarvitava apuneuvo löytynee tehtäväpohjassa olevasta `Auth`-palvelusta (`firebase.auth.service.js`). Tiedostossa `app.js` olevasta koodista selvinnee, miten tapahtuu "*AUTH_REQUIRED*" -tekstin tulostus ja  *Hae numeroita* -näkymän esiintuonti samassa tilanteessa.

[kohta-17.5]: {{site.baseurl}}/weso/#17.5-Turvallisuus-ennen-kaikkea:-authentikaatio-Firebasen-avulla

#### 9. Tietojen haku Firebase -tietokannasta

Tallenna Firebase -tietokantaan sen konsolin avulla jotakin lähtödataa edellä kohdan [Tietokanta](#tietokanta) esittämässä muodossa.

Muokkaa `Muistio` -palvelua (`firebase.db.service.db`) ja `SearchController` -kontrolleria (`search.controller.js`) siten, että Firebase-tietokannan tietoja näkyy *Hae numeroita* -näkymässä.

*Vihjeitä*

Sovellukseen upotettua dataa käytettäessä, tietojen haku kontrolleriin voidaan toteuttaa seuraavan periaatteen mukaan:

{% highlight javascript %}
  tiedot = kohde.hae(hakuEhto);
{% endhighlight %}

Kun tietojen haku tapahtuu verkon yli, paluudata ei ole välittömästi käytettävissä. Siten kohde, jolle pyyntö esitetään, tyypillisesti kutsuu sille välitettyä funktiota datan ollessa käytettävissä, esim. periaatetasolla seuraavasti:

{% highlight javascript %}
  kohde.hae(hakuEhto, function(paluuData){
      tiedot = paluuData;
  });
{% endhighlight %}

Kontrollerissa oletettavasti tietojen haku tässä toteutetaan tarkkailijassa (`$watch`). Tarkkailija laukeaa heti myös alussa, jolloin hakuehtona oleva henkilön nimi on määrittelemätön ([undefined][undefined]). Tietojen haku tässä tilanteessa kannattanee estää sopivalla if-rakenteella.

[undefined]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined

Tehtäväpohjan runko (`firebase.db.service.js`) ehdottaa käytettäväksi Firebase -rajapinnan [$firebaseObject][$firebaseObject] -oliota tietojen välitykseen sovelluksen ja tietokannan välillä. Olio tuhotaan kayttäjän ulos kirjautumisen yhteydessä (ks. rungon lopussa oleva koodi). Siten olio on luotava uudelleen, ennen kuin rajapintaa käytetään seuraavan kerran uudelleen. Olion luonti voidaan tässä tehdä `annaNumerot` -metodissa tilanteessa, jossa oliota ei vielä ole tai se on merkitty tuhotuksi.

`$firebaseObject`-olion [$loaded][$loaded] -metodin avulla voidaan varmistua viitattujen  tietokannan tietojen olevan käytetävissä (ks. käsikirjan [ao. kohdan][$loaded] yhteydessä oleva esimerkki). Haettu data voidaan palauttaa `then` -metodilla, joka ketjutetaan `$loaded`-kutsun perään.  Ketjuun voi liittää myös virheenkäsittelyn, jonka osalta tässä voi hyödyntää  tehtäväpohjan `handleError` -funktiota.

[$firebaseObject]: https://github.com/firebase/angularfire/blob/master/docs/reference.md#firebaseobject

[$loaded]: https://github.com/firebase/angularfire/blob/master/docs/reference.md#loaded

`$firebaseObject`-olion dataan voidaan viitata taulukkonotaatiolla "tavallisten" JavaScript -olioiden tapaan. Esim., jos `muistio` on  `$firebaseObject`, henkilön *bart* puhelinnumerot sisältävä olio saadaan seuraavasti: `muistio['bart']`.

#### 10. Firebase -tietokannan tietojen ylläpito

Muokkaa `Muistio` -palvelua (`firebase.db.service.db`) siten, että näkymien kautta puhelinmuistioon tehdyt muutokset päivittyvät Firebase-tietokantaan.

*Vihjeitä*:

`$firebaseObject`-olion sisältämä data ei synkronoidu automaattisesti Firebase-tietokannan kanssa. Siten datan muutoksen jälkeen on tukeuduttava olion [$save][$save] -metodin käyttöön

[$save]: https://github.com/firebase/angularfire/blob/master/docs/reference.md#save

Datan muutos olioon hoituu taulukkonotaatiolla. Esim. uuden numeron lisääminen henkilölle *bart* tapahtuu seuraavasti: `muistio['bart']['_444']='444'` (olettaen, että *muistio* on`$firebaseObject`, joka sisältää jo `bart` -attribuutin ja, että tietokannan rakenne on [edellä esitetyn](#tietokanta) kaltainen).

#### *Vaihe III*


#### 11. Palauta tehtävän ratkaisu

**Palauta** tehtävän ratkaisusta tiedostot `route.config.js`, `firebase.db.service.js`, `search.controller.js` sekä `search.view.html`, joiden rungot löytyvät tehtäväkohjan `todo`-kansiosta. Varmista ennen palautusta, että sovellus toimii odotetusti. Jos pohjakoodi sisältää testejä, varmista niiden läpimeno ilman virheilmoituksia.  Varmista myös, että selaimen konsolille ei tule virheilmoituksia sovellusta käytettäessä.

### Lisätietoja

[Tehtävään liittyvä keskustelu](https://moodle2.tut.fi/mod/forum/discuss.php?d=70318)   
[Firebase -dokumentaatio](https://firebase.google.com/docs/)   
[AngularFire API Reference](https://github.com/firebase/angularfire/blob/master/docs/reference.md)   
[AngularFire Guide](https://github.com/firebase/angularfire/blob/master/docs/guide/README.md)   


#### Alaviitteet

{% endcomment %}
