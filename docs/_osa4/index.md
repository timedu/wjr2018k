---
layout: collection_index
permalink: /:collection/index.html
modified_at: 22.4.2018
---


Tässä osassa jatketaan [edellisen osan](../osa3) [AngularJS][AngularJS]-teemaa. Esillä on jo edellä käsiteltyjä aiheita kuten sovelluksen jäsentäminen näkymiksi ja kontrollereiksi sekä näiden välinen kommunikointi ns. näkyvyysalueen (scope) kautta. Tämä osan uusia tarkastelukohteita ovat palveluiden laatiminen ja injektointi sovelluksen käyttöön sekä teknisesti [yksisivuiset sovellukset][spa], jotka käyttäjän näkökulmasta ovat monisivuisia. Esillä on myös pilviplvelussa toimiva tietokanta, jota käytetään sen rajanpinnan tarjoamien, sovellukseen injektoitavien, palvelujen kautta.


[AngularJS]: https://angularjs.org
[spa]: https://en.wikipedia.org/wiki/Single-page_application


{% assign weso = 'http://web-selainohjelmointi.github.io' %}

[Web-selainohjelmointi]({{weso}}) käsittelee 
[AngularJS](https://docs.angularjs.org/guide/introduction)-sovelluskehystä luvuissa
[12. Sovelluksen rakenteen hallinta: AngularJS]({{weso}}/#12-Sovelluksen-rakenteen-hallinta:-AngularJS),
[13. Jatketaan keskustelua palvelimen kanssa: Firebase]({{weso}}/#13-Jatketaan-keskustelua-palvelimen-kanssa:-Firebase),
[15. Reititys Angularissa]({{weso}}/#15-Reititys-Angularissa) ja
[17. Suurempi Angular-sovellus: Elokuvakirjasto]({{weso}}/#17-Suurempi-Angular-sovellus:-Elokuvakirjasto).   


### Tehtävät

Tehtävissä palataan  aiemmin ([Osa 1](../osa1)) esillä olleeseen puhelinmuistio -sovellukseen, jonka ominaisuuksia kehitetään nyt AngularJS:n avulla. Osa sisältää kuusi tehtävää:

{% include exercises_list.md %}


[Tehtävässä 4.1](tehtava41)  jäsennetään puhelinmuistio -sovellus siten, että sen näkymä ja kontrolleri on toteutettu AngularJS:n avulla. [Tehtävässä 4.2](tehtava42) sovelluksen dataa ylläpitävästä moduulista laaditaan erillinen palvelu, joka injektoidaan kontrollerin käyttöön. [Tehtävässä 4.3](tehtava43) rakennetaan sovelluksen painikkeisiin liitettävä direktiivi, joka määrää panikkeen otsikon ja samalla klikkaukseen liityvän käsittelijän. [Tehtävässä 4.4](tehtava44) sovellus jaetaan kolmeen erilliseen näkymään ja määritellään erillisen reitityskonfiguraation avulla osoitteet, joissa kukin näkymä tulee esiin. 

[Tehtävässä 4.5](tehtava45) perustetaan [Firebase][Firebase]-palveluun kokeiluluonteinen tietokanta ja kytketään se AngularJS-sovellukseen siten, että se esittää näkymässään tietokannasta luettuja tietoja. Sovellus toimii niin, että muutettaessa palvelun hallintakonsolin kautta tietokannan tietoja, tiedot muuttuvat sovelluksen sivulla ilman sivun uudelleenlatausta. [Tehtävässä 4.6](tehtava46) laaditaan puhelinmuistio -sovellus siten, että sen data talletetaan Firebase-tietokantaan. Sovellukseen liitetään samalla myös tunnistautuminen, joka sekin tukeutuu Firebaseen. 

[Firebase]: https://firebase.google.com

