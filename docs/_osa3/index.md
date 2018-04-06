---
layout: collection_index
permalink: /:collection/index.html
modified_at: 6.4.2018
---

Vuonna 2012[^release] julkaistu [AngularJS][angularjs] on edelleenkin [suosituimpien][popularity] selainpään sovelluskehysten joukossa. Se on ominaisuuksiltaan [edellisessä osassa](../osa2) tarkasteltua *Backbone:a* huomattavasti laajempi. *AngularJS*-pohjaisten sovellusten keskeisiä rakenneosia ovat *mallit*, *näkymät* ja *kontrollerit*:

[angularjs]:https://docs.angularjs.org/guide/introduction
[popularity]: https://hotframeworks.com/languages/javascript

[^release]: <small>[Version 1.0.0](https://github.com/angular/angular.js/blob/master/CHANGELOG.md#100-temporal-domination-2012-06-13) julkaisuvuosi; tätä aikaisempia julkaisuja vuodesta 2010 lähtien</small>

>
Model - the data shown to the user in the view and with which the user interacts  
View - what the user sees (the DOM)  
Controller - the business logic behind views  
<cite><small>
[[AngularJS Developer Guide](https://docs.angularjs.org/guide/concepts)]
</small></cite>  

*Näkymän* perustana on *template*, joka muodostuu html-merkkauksesta sitä täydenttävistä *direktiiveistä*. AngularJS-sovelluksissa data välittyy *mallista* *näkymään* ja päinvastoin ilman, että se edellyttää JavaScript-koodin laatimista:

![Data_Binding](https://docs.angularjs.org/img/Two_Way_Data_Binding.png "Data_Binding"){: style="display: block; margin: auto; margin-top: 10px; width: 350px; padding: 5px;"}
<cite><small>
[[AngularJS Developer Guide](https://docs.angularjs.org/guide/databinding)]
</small></cite>  

*AngularJS*:n vuonna 2016 julkaistu seuraaja kulkee nimellä [Angular](https://angular.io). Tiettävästi kehittäjien keskuudessa [kritiikkiä][critic] on herättänyt se, että *Angular* ei ole taaksepäin yhteensopiva jonkinlaisen de-facto aseman saavuttaneen *AngularJS*:n kanssa[^angularjs-vs-angular]. *AngularJS:n* seuraava versio (1.7.0) [julkaistaan][next-release] kuluvan vuoden kesäkuun lopussa.

[critic]: https://jaxenter.com/angular-2-0-announcement-backfires-112127.html
[next-release]: https://blog.angular.io/stable-angularjs-and-long-term-support-7e077635ee9c

[^angularjs-vs-angular]: <small>[Comparison Between: Angular 1 Vs Angular 2 Vs Angular 4][versus-3], [Angular vs Angular 2][versus-1], [Angularjs Vs Angular2 | What’s The Difference?][versus-2]</small>

[versus-1]: https://stackoverflow.com/questions/34114593/angular-vs-angular-2
[versus-2]: https://www.dunebook.com/angularjs-vs-angular2-whats-the-difference/
[versus-3]: https://www.angularminds.com/blog/article/comparison-difference-between-angular1-vs-angular2-vs-angular4.html

### Tehtävät

Tämän osan kahdeksan tehtävää ovat modifikaatiota lähteen[^lisenssi] luvun [12 Sovelluksen rakenteen hallinta: AngularJS](http://web-selainohjelmointi.github.io/#12-Sovelluksen-rakenteen-hallinta:-AngularJS) tehtävistä 27-34.

[^lisenssi]: <small>[Lähdemateriaali](http://web-selainohjelmointi.github.io) on lisensoitu Creative Commons BY-NC-SA-lisenssillä, joten sitä voi käyttää ja levittää  vapaasti, kunhan alkuperäisten tekijöiden nimiä ei poisteta. Jos materiaaliin tekee muutoksia ja levittää muunneltua versiota, se täytyy lisensoida samanlaisella vapaalla lisenssillä. Materiaalien käyttö kaupalliseen tarkoitukseen on ilman erillistä lupaa kielletty. Lähteenä olevan materiaalin ovat laatineet Kalle Ilves ja Arto Vihavainen.</small>

{% include exercises_list.md %}

[Tehtävässä 3.1](tehtava31) täydennetään pohjassa olevaa *templatea* siten, että data siirtyy *näkymässä* olevista tekstikentistä *malliin* ja sieltä näkymässä olevan elementin sisällöksi. Tämä voidaan toteuttaa ilman JavaScript-koodin kirjoittamista. Tehtävässä tosin laaditaan myös yksinkertainen *kontrolleri*, joka suorittaa *mallin* datan asettamisen alkuarvoonsa. [Tehtävässä 3.2](tehtava32) laaditaan *template*, joka muodostaa näkymän taulukkomuotoisen datan perusteella. Lähtökohtana on html-merkkaus, jota täydennetään *AngularJS*-direktiiveillä, ja jonka vakiosisältö korvataan viittauksilla mallin dataan.

[Tehtävässä 3.3](tehtava33) muodostetaan *template*, joka suodattaa *mallin* datajoukkoa siten, että ainoastaan tiettyjen tekstikenttien määräämä osa datasta esitetään *näkymässä*. Ominaisuuden toteuttaminen ei edellytä JavaScript-koodin laatimista. [Tehtävässä 3.4](tehtava34) toteutetaan *template*, johon perustuva *näkymä* kelpoistaa käyttäjän lomakkeelle syöttämiä tietoja. Kelpoistuksessa hyödynnetään myös erästä AngularJS:n laajennusta. Perusmuodossaan tämäkin voidaan toteuttaa ilman JavaScriptia, mutta tässä laaditaan ohjelmointia edellyttävä eräs kelpoistusta tukeva direktiivi, joka tosin on pohjassa jo melkein valmiina.

[Tehtävän 3.5](tehtava35) painopiste on *kontrollerissa*, johon laaditaan joukko *näkymästä* kutsuttavia metodeja. Myös [Tehtävän 3.6](tehtava36) keskittyy *kontrolleriin*, johon rakennetaan *mallin* datan muutoksia seuraavia tarkkailijoita. Tehtävässä tulee esiin myös, miten kontrolleri voi toimintansa tueksi ottaa käyttöön erillisiä palveluja. [Tehtävän 3.7](tehtava37) muistilista-sovellus on muihin tehtäviin verrattuna jonkin verran laajempi. Tehtävän kokoaa yhteen jo edellisissä  tehtävissä sovellettuja *AngularJS*-ominaisuuksia. [Tehtävän 3.8](tehtava38) rakennetaan *direktiivi*, jonka asettaminen *templateen* tuo näkymään liukusäädin-tyyppisen käyttöliittymäelementin.  

### Lisätietoja

[AngularJS Developer Guide](https://docs.angularjs.org/guide)  
[AngularJS Tutorial](https://docs.angularjs.org/tutorial)   
[General Learning Resources](https://docs.angularjs.org/guide/external-resources#general-learning-resources)  







<br/>
