---
layout: collection_index
permalink: /:collection/index.html
kesken: 1
modified_at: 3.4.2018
---

[AngularJS](https://docs.angularjs.org/guide/introduction)

{% comment %}

> [Angular](https://angular.io) is a platform that makes it easy to build applications with the web. Angular combines declarative templates, dependency injection, end to end tooling, and integrated best practices to solve development challenges. Angular empowers developers to build applications that live on the web, mobile, or the desktop.


> Olemme tähän mennessä onnistuneesti pystyneet esittämään sovelluksemme dataa käyttöliittymässä ja jopa välittämään käyttöliittymästä tehtyjä muutoksia sovelluslogiikkaan.
[Mustache](https://mustache.github.io)
 tekee datan esittämisestä näkymässä melko helppoa, mutta kuten olet ehkä huomannut, datan muokkaaminen näkymän kautta ei ole aivan niin helppoa. Ongelmat ilmenevät etenkin sovelluksen kasvaessa, jolloin sen rakenteesta tulee aina vain sekavampi. Rakennetta selkeyttää huomattavasti käyttöliittymän erottaminen sovelluksen datasta, johon jo mainittu MVC-arkkitehtuuri pyrkiikin. Selkeän MVC-arkkitehtuurin aikaansaaminen on kuitenkin yllättävän vaikeaa, jos työkalut eivät ole oikeat.
>
> Apuun tulee suuren suosion saavuttanut [AngularJS](https://angularjs.org)
MVW-[sovelluskehys](https://fi.wikipedia.org/wiki/Ohjelmistokehys).
Edellisessä lauseessa ei ole kirjoitusvirhettä, Angularia ei voi rajata pelkäksi MVC-sovelluskehykseksi (vaikkakin niin usein tehdään), vaan tarkempi termi onkin "Model View Whatever". Se siis esittää mallia näkymässä ja välittää näkymässä tehtyjä muutoksia takaisin malliin. Mitä mallin ja näkymän rajapinnassa tapahtuu, on ohjelmoijan itsensä päätettävissä.
>
> Mikä Angularissa on hienoa, on se, että se tekee luonteeltaan staattisesta HTML:stä dynaamista, jolloin malli on sekä helppo esittää näkymässä, että helppo muokata näkymän kautta. Yksinkertaisia sovelluksia voidaan saada aikaan kirjoittamatta riviäkään JavaScriptiä.

Edellä oleva lainaus on poimittu [kurssilukemiston]({{site.baseurl}}/weso/) luvun 12
([Sovelluksen rakenteen hallinta: AngularJS]({{site.baseurl}}/weso/#12-Sovelluksen-rakenteen-hallinta:-AngularJS)) alusta. Myös kaikki tämän osan tehtävät perustuvat kurssilukemistoon.

{% endcomment %}


### Tehtävät

Tehtävät on poimittu lähteen[^lisenssi] luvusta [12 Sovelluksen rakenteen hallinta: AngularJS](http://web-selainohjelmointi.github.io/#12-Sovelluksen-rakenteen-hallinta:-AngularJS).


[^lisenssi]: <small>[Lähdemateriaali](http://web-selainohjelmointi.github.io) on lisensoitu Creative Commons BY-NC-SA-lisenssillä, joten sitä voi käyttää ja levittää  vapaasti, kunhan alkuperäisten tekijöiden nimiä ei poisteta. Jos materiaaliin tekee muutoksia ja levittää muunneltua versiota, se täytyy lisensoida samanlaisella vapaalla lisenssillä. Materiaalien käyttö kaupalliseen tarkoitukseen on ilman erillistä lupaa kielletty. Lähteenä olevan materiaalin ovat laatineet Kalle Ilves ja Arto Vihavainen.</small>

{% include exercises_list.md %}

{% comment %}


Viimeinen tehtävistä ([4.7](tehtava47)) on muita jonkin verran laajempi muistuttaen ominaisuuksiltaan kurssin edellisten osien tehtävissä eri periaattein toteutettua Puhelinmuistio-sovellusta. Muut tehtävät keskittyvät *AngulaJS*-sovelluskehyksen yksittäisten ominaisuuksien esittelyyn.

[Tehtävässä 4.1](tehtava41) voidaan todeta, miten *AngularJS* hoitaa datan siirtymisen *näkymästä* *malliin* ja päinvastoin ilman JavaScript-koodin kirjoittamista. Tehtävässä tosin laaditaan myös yksinkertainen *kontrolleri*, joka suorittaa *mallin* datan asettamisen alkuarvoonsa.

[Tehtävä 4.2](tehtava42) esittelee *AngularJS* -näkymien muodostamisessa käytettävää template -kieltä, joka syntaksiltaan muistuttaan *Mustachea*. Angularia käytettäessä templatet laaditaan osaksi merkkausta siten, että merkkaukseen sisällytetään Angularin ymmärtämiä ns. direktiivejä, jotka voivat esiintyä lähdekoodissa html -elementtien attribuutteina tai omina elementteinään.

[Tehtävässä 4.3](tehtava43) tulee esiin, miten *mallin* datajoukkoa voidaan suodattaa *näkymässä* ilman JavaScript-koodaamista. [Tehtävässä 4.4](tehtava44) kelpoistetaan käyttäjän lomakkeelle syöttämät tiedot. Perusmuodossaan tämäkin voidaan toteuttaa ilman JavaScriptia. Tehtävässä hyödynnetään kelpoistuksessa myös erästä Angularin laajennusta sekä laaditaan oma kelpoistusta tukeva direktiivi. Viimeksi mainittu edellyttää JavaScript -koodia, mutta se on pohjassa jo melkein valmiina.

[Tehtävän 4.5](tehtava45) painopiste on kontrollerissa, johon laaditaan joukko näkymästä kutsuttavia metodeja. Myös [Tehtävän 4.6](tehtava46) keskittyy kontrolleriin, johon rakennetaan mallin datan muutoksia seuraavia tarkkailijoita. Tehtävässä tulee esiin myös, miten kontrolleri voi toimintansa tueksi ottaa käyttöön erillisiä palveluja.

{% endcomment %}


<br/>
