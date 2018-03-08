---
layout: site_page
title: Osan 1 tehtävien pohjakoodista
modified_at: 8.3.2018
---

Tehtävien 1.1 - 1.4 pohjilla on seuraavanlainen rakenne:

~~~
[css]
[img]
[js]
    [vendor]
    app.js
[spec]
[todo]
    puhelinmuistio.js
SpecRunner.html
index.html
~~~

Rakennettava sovellus muodostuu kolmesta tiedostosta: `index.html`, `js/app.js` ja `todo/puhelinmuistio.js`. Tehtävän ratkaisu laaditaan näistä viimeksi mainittuun. `index.html` ja `app.js` ovat pohjassa valmiina. Pohjan muut hakemistot ja tiedostot liittyvät hyödynnettäviin ohjelmakirjastoihin ja testeihin.


Tiedostossa `index.html` on käyttöliittymä ja `app.js` on määritelty käyttöliittymässä olevien painikkeiden `click`-tapahtumien käsittelijät. Käyttöliittymää on jonkin verran muotoiltu [Bootstrap][Bootstrap]-kirjaston css-luokilla ja tiedostossa `app.js` on hyödynnetty [jQuery][jQuery]-kirjastoa tarvittavan koodimäärän tiivistämiseksi.

[Bootstrap]: http://getbootstrap.com
[jQuery]: https://jquery.com


Tehtävien yhteydessä laadittava osuus sovelluksesta (`puhelinmuistio.js`) ei ole riippuvainen muista tiedostoista (`app.js`, `index.html`). Seuraavassa on kuitenkin taustaksi jokunen sana näiden sisältämästä koodista.

#### Käyttöliittymä (index.html)


![Käyttöliittymä](../img/puhelinmuistio_ui.png "Käyttöliittymä"){: style="display: block; margin: auto; margin-top: 10px; width: 500px;"}

<small>Kuva 1. Käyttöliittymä.</small>



{% highlight html linenos %}

<div class="container mt-3">
   <h2>Puhelinmuistio <span></span></h2>
   <div class="border  rounded p-2">
      <div class="form-row">
         <div class="col-sm">                  
            <label for="nimi">Nimi</label>
            <input class="form-control" id="nimi"/>
            <button class="btn btn-primary  mt-2" id="etsi">Etsi</button>                  
         </div>
         <div class="col-sm">
            <label for="numero">Numero</label>
            <input type="tel" class="form-control" id="numero"/>
            <button class="btn btn-primary mt-2" id="lisaa">Lisää</button>
         </div>
      </div>
   </div>
   <div id="luettelo" class="mt-2 p-2">
      <div class="row border-bottom">
         <div class="col-sm-5"><h5>Nimi</h5></div>
         <div class="col-sm-5"><h5>Numero</h5></div>
      </div>
      <div id="numerot"></div>            
   </div>
</div>        

{% endhighlight %}

<small>Listaus 1. Käyttöliittymän merkkaus.</small>


Käyttöliittymän merkkauksesta (*Listaus 1*) muuhun osaan sovelluksesta liittyvät
rivit 7, 8, 12, 13 ja 22, jotka on esitetty hieman pelkistettynä *Listauksessa 2*.

{% highlight html %}

  <input id="nimi"/>
  <button id="etsi">Etsi</button>

  <input id="numero"/>
  <button id="lisaa">Lisää</button>

  <div id="numerot"></div>            

{% endhighlight %}

<small>Listaus 2. </small>

`input`-elementtien kautta sovellukselle välitetään tietoja ja `button`-elementtien klikkaukset toimivat herätteinä toimintojen käynnistymiselle.

`div`-elementin (*id="numerot"*) sisältönä esitetään puhelinmuistioon talletettuja tietoja (*Listaus 3*), joiden yhteydessä on painikkeen tiedon poistamiseksi muistiosta. Tämä osa dokumentista muodostuu dynaamisesti sovelluksen käytön yhteydessä.

{% highlight html %}

  <div id="numerot">

      <div class="row mt-1">
          <div class="col-sm-5">Flanders</div>
          <div class="col-sm-5">0600-14067815</div>
          <div class="col-sm">
              <button class="btn btn-danger btn-sm">x</button>                  
          </div>               
      </div>   

  </div>            

{% endhighlight %}

<small>Listaus 3. </small>

#### Sovelluksen alustaminen (app.js)

Moduuli `app.js` (*Listaus 4*) määrittelee [jQuery][jQuery]-kirjaston tukemana käyttöliittynässä oleville painikkeille,  *Etsi*, *Lisää* ja *x* (poista), niiden klikkaukseen liittyvät toiminnot.


{% highlight js linenos %}

$(() => {

    const muistio = new Puhelinmuistio();

    $('#etsi').click(() => {
        let nimi = $('#nimi').val().trim();
        esitaNumerot(nimi);
    });

    $('#lisaa').click(() => {
        let nimi = $('#nimi').val().trim();
        let numero = $('#numero').val().trim();        
        muistio.lisaaNumero(nimi, numero);
        esitaNumerot(nimi);
    });

    let esitaNumerot = nimi => {
        $('#numerot div').remove();
        muistio.annaNumerot(nimi).forEach(numero => {

            const row = $('<div/>').addClass('row mt-1')
                .appendTo('#numerot');

            $('<div/>').addClass('col-sm-5').text(nimi).appendTo(row);
            $('<div/>').addClass('col-sm-5').text(numero).appendTo(row);
            $('<div/>').addClass('col-sm').appendTo(row);

            $('<button/>').addClass('btn btn-danger btn-sm')
                .data('nimi', nimi)
                .data('numero', numero)
                .appendTo(row.find(':last-child'))           
                .text('x')
                .click(e => {
                    let nimi = $(e.target).data('nimi');
                    let numero = $(e.target).data('numero');                                
                    muistio.poistaNumero(nimi, numero);
                    esitaNumerot(nimi);
                });
        });
    };
});


{% endhighlight %}

<small>Listaus 4. </small>


*Listauksen 4* riveillä 3, 13, 19 ja 36 esiintyy tehtävissä laadittavan ratkaisun käyttöä:


{% highlight js%}

const muistio = new Puhelinmuistio()
muistio.lisaaNumero(nimi, numero)
muistio.annaNumerot(nimi)
muistio.poistaNumero(nimi, numero)

{% endhighlight %}

<small>Listaus 5. </small>

*Listaukssa 4* koodi on sisällytetty funktioon, joka annetaan jQuery-kirjaston sisältämän *jQuery*-funktion (`$`) parametriksi:

{% highlight js %}

$(() => {
  ...
});

{% endhighlight %}

<small>Listaus 6. </small>

`$`-funktion parametrina oleva funktio suoritetaan, kun sivu on kokonaisuudessaan latautunut selaimeen. Parametrina toimiva funktio on esitetty ns. [nuolinotaatiolla][nuoli]. Saman asian voisi kuvata perinteisemmin seuraavasti:

[nuoli]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions


{% highlight js %}

$(function() {
  ...
});

{% endhighlight %}

<small>Listaus 7. </small>

*Listauksessa 4* riveillä 5-8 määritellään *jQuery*:n avulla nuolinotaatiota käyttäen *Etsi*-painikkeelle sen *click*-tapahtumaan liittyvä käsittelijä:

{% highlight js %}

$('#etsi').click(() => {
    let nimi = $('#nimi').val().trim();
    esitaNumerot(nimi);
});

{% endhighlight %}

<small>Listaus 8. </small>

Tässä`$`-funktion parametrina on css-syntaksia noudattava [valitsin][valitsin], jonka avulla *Etsi*-painike paikantuu dokumentissa. `$`-funktion kutsu palautaa *jQuery*-objektin, jolla taas on mm. metodi [click][click]. Tässä metodille parametrina annettu funktio suoritetaan, kun *Etsi*-painiketta klikataan. Funktio on kuvattu nuolinotaatiolla, mutta sen voisi esittää perinteisemmin seuraavasti:

[valitsin]: http://api.jquery.com/category/selectors/
[click]: http://api.jquery.com/click/

{% highlight js %}

$('#etsi').click(function(){
    ...
});

{% endhighlight %}

<small>Listaus 9. </small>

*Listauksessa 8* esitetyssä funktiossa on kaksi lausetta, joista ensimmäisenä olevaan sijoituslauseeseen voisi taas kiinnittää huomiota:

{% highlight js %}

let nimi = $('#nimi').val().trim();

{% endhighlight %}

<small>Listaus 10. </small>

Sijoituksen vasemmalla puolella oleva [let][let] määrittelee lohkon sisäisen muuttujan. Oikealla puolella hyödynnetään taas *jQueryä*, jolla paikannetaan *nimi*-tekstikenttä ja poimitaan kentässä oleva teksti merkkijonon palauttavalla [val][val]-metodilla. Palautuvasta merkkijonosta eliminoidaan vielä tyhjät merkit alusta ja lopusta merkkijonon [trim][trim]-metodilla.  

[let]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let
[val]: http://api.jquery.com/val/
[trim]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/Trim

*Listauksessa 4* painikeiden *Etsi* ja *Lisää* `click`-tapahtumien käsittelijöiden määrittelyiden jälkeen *riveillä 17-40* on määritelty funktio `esitaNumerot`, jota molemmat tapahtumakäsittelijöistä kutsuvat:

{% highlight js linenos %}

let esitaNumerot = nimi => {
    $('#numerot div').remove();
    muistio.annaNumerot(nimi).forEach(numero => {

        const row = $('<div/>').addClass('row mt-1')
                .appendTo('#numerot');

        $('<div/>').addClass('col-sm-5').text(nimi).appendTo(row);
        $('<div/>').addClass('col-sm-5').text(numero).appendTo(row);
        $('<div/>').addClass('col-sm').appendTo(row);

        $('<button/>').addClass('btn btn-danger btn-sm')
                .data('nimi', nimi)
                .data('numero', numero)
                .appendTo(row.find(':last-child'))
                .text('x')
                .click(e => {
                    let nimi = $(e.target).data('nimi');
                    let numero = $(e.target).data('numero');
                    muistio.poistaNumero(nimi, numero);
                    esitaNumerot(nimi);
                });
    });
};

{% endhighlight %}

<small>Listaus 11. </small>

*Listauksessa 11*  esitetty funktio poistaa ensin dokumentista puhelinmuistion tiedoille varatulta alueelta kaikki elementit (*rivi 2*), lukee muistiosta henkilön numerot (*rivi 3*) ja rakentaa sitten kuhunkin numeroon liittyvät elementit asettaen ne osaksi dokumenttia (vrt. *Listaus 3*).


Myös tässä funktion voisi nuolinotaation sijaan määritellä seuraavilla tavoilla (*Listaukset 11 ja 12*):

{% highlight js %}

let esitaNumerot = function (nimi) {
  ...
};

{% endhighlight %}

<small>Listaus 12. </small>


{% highlight js %}

function esitaNumerot(nimi) {
  ...
};

{% endhighlight %}

<small>Listaus 13. </small>

<br/>
