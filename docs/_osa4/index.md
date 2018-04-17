---
layout: collection_index
permalink: /:collection/index.html
modified_at: 16.4.2018
kesken: 1
julkaisu: 18.4.2018
---

[AngularJS](https://docs.angularjs.org/guide/introduction)


{% comment %}

Kurssin [edellisessä osassa](../osa3) tutustuttiin jo [AngularJS][AngularJS] -sovelluskehykseen. Todettiin mm., että Agularissa tiedot siirtyvät ilman ohjelmointia mallin ja näkymän välillä kontrollerijohtaisella näkyvyysalueella, johon voi sisällyttää myös näkymästä kutsuttavissa olevaa toiminnallisuutta. Mallin datalle asetettiin myös tarkkailijoita, jotka reagoivat mallin datan muutoksiin.

[AngularJS]: https://angularjs.org

Tämä osa jatkaa vielä Angular-teemalla. Edellisen osan tehtävissä hyödynnettiin jo valmiita Angular-palveluja. Tässä osassa esitellään palvelu, jonka avulla sovellus voi olla yhteydessä verkossa toimivaan tietokantaan. Osassa tutustutaan myös siihen, miten voidaan laatia omia palveluja ja injektoida niitä sovelluksen muiden moduulien käyttöön. Angular-näkymät perustuvat diretiiviiveihin, jotka voivat esiintyä merkkauksessa elementteinä tai elementtien attribuutteina. Tämä osa esittelee, miten kehitetään omia  näkymissä käytettäviä direktiivejä. Osan yhtenä teemana on vielä sovelluksen reitytys, johon [kurssilukemisto][weso] johdattelee seuraavasti:

[weso]: {{site.baseurl}}/weso/

> Isompi sovellus on usein jaettu useaan eri näkymään, jotka löytyvät eri poluista, kuten `/elokuvat`, `/elokuvat/1` ja `elokuvat/uusi`. Perinteisesti sovelluksen polut määritetään palvelinpuolen sovelluksessa, mutta kasva trendi on toteuttaa ainakin osa sovelluksen reitityksestä selainpuolella, jolloin sovelluksessa uuteen polkuun siirtyminen ei rasita niin paljon palvelinta. Näitä sovelluksia kutsutaan nimellä *Single-page application*.

[AngularJS][AngularJS] on esillä [kurssilukemiston][weso] luvuissa
[12. Sovelluksen rakenteen hallinta: AngularJS]({{site.baseurl}}/weso/#12-Sovelluksen-rakenteen-hallinta:-AngularJS),
[13. Jatketaan keskustelua palvelimen kanssa: Firebase]({{site.baseurl}}/weso/#13-Jatketaan-keskustelua-palvelimen-kanssa:-Firebase),
[15. Reititys Angularissa]({{site.baseurl}}/weso/#15-Reititys-Angularissa) ja
[17. Suurempi Angular-sovellus: Elokuvakirjasto]({{site.baseurl}}/weso/#17-Suurempi-Angular-sovellus:-Elokuvakirjasto).   


{% endcomment %}


### Tehtävät

{% comment %}


Tämän osan tehtävissä palataan jo edellisissä osissa esillä olleeseen puhelinmuistio -sovellukseen, jonka ominaisuuksia kehitetään nyt AngularJS:n avulla. Osa sisältää kuusi tehtävää:

{% endcomment %}


{% include exercises_list.md %}

{% comment %}

[Tehtävä 4.1](tehtava41) kertaa jo [kurssin edellisessä osassa](../osa3) esiin tulleita asioita. Tehtävässä muokataan aikaisemmin toteutettu sovellus siten, että sen näkymä ja kontrolleri on toteutettu Angularilla. [Tehtävässä 4.2](tehtava42) sovelluksen dataa ylläpitävästä Muistio-moduulista laaditaan erillinen palvelu, joka injektoidaan kontrollerin käyttöön. [Tehtävä 4.3](tehtava43) esittelee, miten direktiivin avulla voidaan määritellä käyttöliittymässä olevan elementin ominaisuuksia. Tehtävässä laadittava, sovelluksen painikkeisiin liitettävä, direktiivi määrää panikkeen otsikon ja samalla klikkaukseen liityvän käsittelijän.

[Tehtävässä 4.4](tehtava44) sovellus jaetaan kolmeen erilliseen näkymään ja määritellään erillisen reitityskonfiguraation avulla osoitteet, joissa kukin näkymä tulee esiin. [Tehtävässä 4.6](tehtava46) injektoidaan sovellukseen palvelu, jonka kautta voidaan käyttää verkossa toimivaa [Firebase][Firebase] -tietokantaa. Sovelluksen data tallennataan tässä palvelun kautta tietokantaan. Sovellukseen liitetään samalla myös tunnistautuminen. [Tehtävä 4.5](tehtava45) on tehtävää 4.6 valmisteleva tehtävä. Tehtävässä 4.5 kytketään sovellus Firebase -tietokantaan ja haetaan sieltä näkymään tietoa.

[Firebase]: https://firebase.google.com

{% endcomment %}
