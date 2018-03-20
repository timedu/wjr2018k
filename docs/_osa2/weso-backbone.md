---
layout: site_page
title: Backbone-kirjastosta
modified_at: 20.3.2018
---

> <small>Sivu on ote Helsingin yliopiston Web-selainohjelmointi -kurssin
materiaalista[^lisenssi][^tekijat]. Alkuperäistä tekstiä on hieman muokattu.</small>

### Sovelluksen rakenteen hallinta: Backbone.js

Kasvavan sovelluksen rakenteen hallinta ei ole helppoa. Selkeään rakenteeseen kuuluu muunmuassa käyttöliittymän ja sovelluksen datan erottaminen toisistaan. Paljon esillä olevat suunnittelumallit kuten *MVC* pyrkivät juuri tähän: käyttöliittymän ei tule tarvita tietää datasta, eikä datan käyttöliittymästä. Rakenteeseen kuuluu myös mekanismi viestien kuljettamiseen käyttöliittymältä datalle ja toisinpäin. JavaScriptissä tähän käytetään usein tapahtumia ja *Observer*-suunnittelumallia.

Tutustutaan seuraavaksi [Backbone.js][backbone]-sovelluskehykseen, joka tarjoaa tuen web-sovellusten rakenteen ylläpitoon. Käytännössä Backbone tarjoaa joukon konstruktori- ja apufunktioita *Model*- ja *View*-olioiden tekemiseen, sekä niiden väliseen kommunikointiin.

[backbone]: http://backbonejs.org/

Backbone tarvitsee toimiakseen [Underscore.js][underscore]-kirjaston, jonka lisäksi se hyötyy huomattavasti [jQuery][jQuery]:stä. Lähdetään luomaan sovellusta kirjojen hallintaan. Sovellus tarjoaa mahdollisuuden kirjojen lisäämiseen ja poistamiseen, sekä kirjojen listaamiseen. Sivun runko on aluksi seuraavanlainen.

[underscore]: http://underscorejs.org/
[jQuery]: https://jquery.com


{% highlight html %}

<!DOCTYPE html>
<html>
<head>
    <title>Kirjasto</title>
    <meta charset="UTF-8">
    <!-- tyylitiedostot -->
</head>
<body>
    <header>
        <h1>Library</h1>
        <nav>
            <ul>
                <li><a href="#">Add</a></li>
                <li><a href="#">List</a></li>
            </ul>
        </nav>
    </header>

    <!-- runko -->
    <section id="main"></section>

    <!-- templatet -->

    <!-- JavaScript-kirjastot -->
    <script src="jquery-1.8.2.min.js"></script>
    <script src="mustache.js"></script>

    <script src="underscore-min.js"></script>
    <script src="backbone-min.js"></script>

    <!-- Omat lähdekooditiedostot -->
</body>
</html>

{% endhighlight %}

<small>Listaus 1.</small>


Sivun lähdekoodeja varten on luotu myös runko, johon lähdekoodit asetetaan.


{% highlight js %}

var library = {
  model: {},
  view:{}
};

{% endhighlight %}

<small>Listaus 2.</small>


#### Näkymä

Tutustutaan näkymien ([View][View]) luontiin *Backbonen* avulla. Backbonessa näkymän konstruktorifunktiot luodaan komennolla `Backbone.View.extend`, jolle annetaan parametrina näkymään liittyviä attribuutteja. Jokainen näkymä liittyy johonkin sivulla olevaan elementtiin (attribuutti `el`), ja näkymään liittyy usein tapahtumia, joita kutsutaan erilaisten tapahtumien yhteydessä (events). Luodaan ensin näkymä valikolle.

[View]: http://backbonejs.org/#View


{% highlight js %}

library.view.NavigationView = Backbone.View.extend({

  // mihin elementtiin näkymä liittyy (header)
  el: $("header"),

  // mitä tapahtumia elementissä kuunntellaan,
  // ja mitä funktioita kutsutaan niiden tapahtuessa
  events: {
      // kun ensimmäistä linkkiä klikataan, kutsu funktiota add
      // vrt. $("header a:nth(0)").click(function() { add() });
      "click a:nth(0)": "add",
      // kun toista linkkiä klikataan, kutsu funktiota list
      "click a:nth(1)": "list"
  },

  // funktio add
  add: function(eventInformation) {
      console.log("add clicked");
      eventInformation.preventDefault();
  },

  // ja funktio list
  list: function(eventInformation) {
      console.log("list clicked");
      eventInformation.preventDefault();
  }

});

{% endhighlight %}

<small>Listaus 3.</small>


Yllä olevassa näkymää varten luodussa koodissa näkymä on elementin `header` sisällä, ja siihen liittyy kaksi tapahtumankuuntelijaa (events). Jos ensimmäistä linkkiä painetaan, tehdään metodikutsu `add`. Toista linkkiä painettaessa tehdään metodikutsu `list`.

Jos haluamme kokeilla ylläolevan näkymän toimintaa, voimme lisätä sen luomiskutsun osaksi *jQuery*:n `$(document).ready` -kutsua. Alla olevassa esimerkissä näkymä luodaan kun sivu on latautunut, jonka jälkeen linkkien painaminen kirjoittaa viestejä selaimen lokiin.


{% highlight js %}

$(document).ready(function() {
  new library.view.NavigationView();
});

{% endhighlight %}

<small>Listaus 4.</small>


Navigaationäkymämme ei oikeastaan tee vielä mitään erityisen mielekästä, joten lisätään sivulle toinen näkymä. Näkymä `AddView` tarjoaa toiminnallisuuden kirjan tietojen lisäämiseen. Luodaan ensin kirjan lisäämiseen käytettävä template. Template sisältää kentät kirjan nimelle, sivujen määrälle, ja isbn-tunnukselle.

{% highlight html %}
<script id="add-book-template" type="text/html">
{% endhighlight %}

{% highlight html %}
{% raw %}

  <h1>Add Book</h1>
  <form>
      <label for="name">Name</label>
      <input type="text" name="name" id="name"/>
      <label for="pages">Pages</label>
      <input type="text" name="pages" id="pages"/>
      <label for="isbn">ISBN</label>
      <input type="text" name="isbn" id="isbn"/>
      <input type="button" value="Add" id="add-book"/>
  </form>

{% endraw %}
{% endhighlight %}

{% highlight html %}
</script>
{% endhighlight %}

<small>Listaus 5.</small>



{% comment %}

{% highlight html %}
{% raw %}

    <script id="add-book-template" type="text/html">

        <h1>Add Book</h1>
        <form>
            <label for="name">Name</label>
            <input type="text" name="name" id="name"/>
            <label for="pages">Pages</label>
            <input type="text" name="pages" id="pages"/>
            <label for="isbn">ISBN</label>
            <input type="text" name="isbn" id="isbn"/>
            <input type="button" value="Add" id="add-book"/>
        </form>

    </script>

{% endraw %}
{% endhighlight %}

<small>Listaus 5.</small>

{% endcomment %}




Backbonen näkymille voi antaa myös `initialize` -parametrin, joka kertoo mitä tehdään näkymää luotaessa. Kun näkymä luodaan, haluamme lisätä yllä olevan templaten sisällön sivulla olevaan "main"-tunnuksella merkittyyn elementtiin. Näkymä AddView kuuntelee myös tapahtumia. Jos sen sisällä olevaa tunnuksella "add-book" merkittyä elementtiä klikataan, kutsutaan metodia `save`. Näkymälle on määritelty myös apufunktio `serialize`, joka luo käytännössä olion lomakkeessa olevasta datasta.


{% highlight js %}

library.view.AddView = Backbone.View.extend({

// mihin elementtiin näkymä liittyy (#main)
el: $("#main"),

// mitä tehdään kun näkymä luodaan (luodaan lisäysnäkymä)
initialize: function() {
    $("#main").html($("#add-book-template").html());
},

// tapahtumat
events: {
    // kun #main -alueessa olevaa #add-book elementtiä painetaan,
    // kutsu metodia save
    "click #add-book": "save"
},

// apufunktio lomakkeen arvojen käsittelyyn
serialize: function() {
    return {
        name: $("#name").val(),
        pages: $("#pages").val(),
        isbn: $("#isbn").val()
    }
},

// funktio, jota kutsutaan, kun lomakkeen nappia painetaan
save: function() {
    var data = this.serialize();
    console.log("Serialized: " + JSON.stringify(data));
    // o-noes, we need to do some stuff with this!
}

});

{% endhighlight %}

<small>Listaus 6.</small>


Muokataan seuraavaksi näkymän `NavigationView` sisältöä siten, että kun linkkiä `Add` klikataan, luodaan uusi instanssi `AddView` -elementistä.


{% highlight js %}

library.view.NavigationView = Backbone.View.extend({

// ...
add: function(eventInformation) {
    new library.view.AddView();
    eventInformation.preventDefault();
},
// ...

{% endhighlight %}

<small>Listaus 7.</small>


Nyt linkin "Add" painaminen näyttää lomakkeen lisäämiseen käytettävän näkymän. Kun lomakkeeseen lisätään dataa, ja nappia "Add" painetaan, näkyy konsolissa (esimerkiksi) seuraavanlainen viesti.

~~~
Serialized: {
  "name":"Harry Potter ja viisasten kivi",
  "pages":"335",
  "isbn":"951-31-1146-6"
}
~~~

<small>Listaus 8.</small>

Datalle ei kuitenkaan vielä tehdä mitään.


#### Malli

Jotta voisimme tehdä kirjadatalle jotain, meillä tulee olla siitä erillinen dataesitys. Luodaan ensin näkymästä täysin erillinen malli, [Model][Model]. Backbone tarjoaa komennon `Backbone.Model.extend`, jonka avulla voidaan luoda konstruktorifunktioita. Komento saa parametrina joukon attribuutteja, joita käsitellään olion luonnin yhteydessä. Luodaan konstruktorifunktio `library.model.Book`, jolla on oma validointifunktio.

[Model]: http://backbonejs.org/#Model

{% highlight js %}

library.model.Book = Backbone.Model.extend({

  validate: function(attributes) {
    if(!attributes.name || attributes.name.length < 1) {
        return "Invalid name: " + attributes.name;
    }

    if(!attributes.pages || attributes.pages.length < 1 || isNaN(Number(attributes.pages))) {
        return "Invalid page count" + attributes.pages;
    }

    if(!attributes.isbn || attributes.isbn.length < 1) {
        return "Invalid isbn " + attributes.isbn;
    }
  }
});

{% endhighlight %}

<small>Listaus 9.</small>


Backbonen mallitoiminnallisuus tarjoaa muunmuassa toiminnallisuuden luokan luontiin attribuuttien avulla. Ylläolevasta luokasta voidaan tehdä ilmentymä antamalla sille olio, jossa on halutut attribuutit. Esimerkiksi alla luodaan kirjaolio, jolla on attribuutit `name`, `pages` ja `isbn`. Attribuutteihin pääsee käsiksi komennolla `get`, ja niitä voi muuttaa komennolla `set`. Metodi `validate` on Backbonen malleihin kuuluva valmis metodi, johon pääsee käsiksi helpon aksessorin `isValid` avulla.


{% highlight js %}

var book = new library.model.Book({
  name:"Harry Potter ja viisasten kivi",
  pages:"335",
  isbn:"951-31-1146-6"
});

console.log("nimi:", book.get("name"));
console.log("sivuja:", book.get("pages"));
console.log("isbn:", book.get("isbn"));

console.log("ok?", book.isValid());

// jätetään isbn tyhjäksi

book = new library.model.Book({
  name:"Harry Potter ja viisasten kivi",
  pages:"335",
  isbn:""
});

console.log("ok?", book.isValid());

{% endhighlight %}

<small>Listaus 10.</small>


Seuraavassa on *Listauksen 10* koodin suorituksen myötä syntyvä tuloste.

~~~~
nimi: Harry Potter ja viisasten kivi
sivuja: 335
isbn: 951-31-1146-6
ok? true
ok? false
~~~~


Mielenkiintoista validoinnissa on se, että se estää huonojen tekojen tekemisen. Esimerkiksi isbn-numeron asettaminen validista versiosta epävalidiksi ei onnistu. Näemme tämän helposti mallista esille saatavan JSON-esityksen avulla. Tuttu `JSON.parse` ei valitettavasti toimi Backbonen olioilla, mutta komento `toJSON` auttaa.


{% highlight js %}

var book = new library.model.Book({
  name:"Harry Potter ja viisasten kivi",
  pages:"335",
  isbn:"951-31-1146-6"
});

console.log(JSON.stringify(book.toJSON()));
book.set("isbn", "");
console.log(JSON.stringify(book.toJSON()));

{% endhighlight %}

<small>Listaus 11.</small>


*Listauksen 11* koodin suoritus aikaansaa seuraavan tulosteen, josta voidaan todeta, että `isbn`-kentän arvo ei ole muuttunut `set`-metodin kutsusta huolimatta.

~~~
{"name":"Harry Potter ja viisasten kivi","pages":"335","isbn":"951-31-1146-6"}
{"name":"Harry Potter ja viisasten kivi","pages":"335","isbn":"951-31-1146-6"}
~~~

Olioita on mahdollista luoda myös antamalla konstruktorifunktiolle parametreina yksittäisiä arvoja. Määrittelemällä `initialize`-metodin oliolle voi lisätä arvoja yksi kerrallaan. Alla on täydennetty ylläolevaa esimerkkiä siten, että sillä on validoinnin lisäksi komento `initialize`.


{% highlight js %}

library.model.Book = Backbone.Model.extend({

  initialize: function(name, pages, isbn) {
    this.set({
        name: name,
        pages: pages,
        isbn: isbn
    });
  },

  validate: function(attributes) {
    ...
  }

});

{% endhighlight %}

<small>Listaus 12.</small>


Nyt olioiden luominen onnistuu seuraavasti:

{% highlight js %}

var book = new library.model.Book(
  "Harry Potter ja viisasten kivi", "335", "951-31-1146-6"
);
console.log(JSON.stringify(book.toJSON()));

{% endhighlight %}

<small>Listaus 13.</small>


~~~
{"name":"Harry Potter ja viisasten kivi","pages":"335","isbn":"951-31-1146-6"}
~~~

**Huom!** Funktion `initialize` määrittely muuttaa konstuktorin toimintaa.
Jos *Listauksessa 12* määritellystä kirjasta luodaan uusi olio  *Listauksessa 11* esitetyllä kutsulla, asetetaan kirjan nimeksi parametrina annettu olio. Oletetaan jatkossa, että kirjaoliolla ei ole erillistä `initialize`-funktiota.


#### Mallin ja näkymän kytkeminen toisiinsa

Kun käytössämme on malli, voimme lisätä sen osaksi sivua. Mallin lisääminen tapahtuu antamalla se parametrina näkymälle. Muokataan sivun luontikutsua siten, että näkymämme `NavigationView` saa konstruktorikutsun yhteydessä parametrina `Book`-olion.


{% highlight js %}

$(document).ready(function() {

  var book = new library.model.Book({
    name:"Harry Potter ja viisasten kivi",
    pages:"335",
    isbn:"951-31-1146-6"
  });

  new library.view.NavigationView({
    model: book
  });

});

{% endhighlight %}

<small>Listaus 14.</small>


Luodaan ensimmäinen versio ListView-oliosta. ListView-olion ensimmäinen versio näyttää yksittäisen kirjan, ja sen käyttämä HTML-template on seuraavanlainen.


{% highlight html %}
<script id="single-book-template" type="text/html">
{% endhighlight %}

{% highlight html %}
{% raw %}

  <p>
    <label for="name">Name</label>
    <span name="name">{{name}}</span><br/>
    <label for="pages">Pages</label>
    <span name="pages">{{pages}}</span><br/>
    <label for="isbn">ISBN</label>
    <span name="isbn">{{isbn}}</span>
  </p>

{% endraw %}
{% endhighlight %}

{% highlight html %}
</script>
{% endhighlight %}

<small>Listaus 15.</small>


Itse ListView näyttää seuraavanlaiselta. Listanäkymään liittyy `this.model`-olio, jonka se saa parametrina konstruktorikutsun yhteydessä. Näkymän toiminnallisuus on yksinkertainen: se näyttää siihen liittyvän mallin sisällön HTML-sivulla.


{% highlight js %}

library.view.ListView = Backbone.View.extend({
  el: $("#main"),
  initialize: function() {
    var html = Mustache.render(
        $("#single-book-template").html(),
        this.model.toJSON()
    );
    $("#main").html(html);
  }
});

{% endhighlight %}

<small>Listaus 16.</small>


Muokataan seuraavaksi NavigationView-näkymää siten, että se luo `ListView`-olion kun `list`-metodia kutsutaan. NavigationView antaa ListView-näkymän konstruktorille parametriksi sen itsensä sisältämän `model`-olion, jonka se saa omassa konstruktorikutsussaan.

{% highlight js %}

library.view.NavigationView = Backbone.View.extend({
// ...
  list: function(eventInformation) {
    new library.view.ListView({
        model: this.model
  });
}
// ...

{% endhighlight %}

<small>Listaus 17.</small>


Nyt näkymä <code>ListView</code> näyttää aina siihen liittyvän kirja-olion tiedot listaa klikattaessa. Sama muutos tulee tehdä myös <code>AddView</code>-näkymän luomiseen.


{% highlight js %}

library.view.NavigationView = Backbone.View.extend({
  // ...
  add: function(eventInformation) {
    new library.view.AddView({
        model: this.model
    });
    eventInformation.preventDefault();
  },
  // ...

{% endhighlight %}

<small>Listaus 18.</small>


**Entä jos kirjan tiedot muuttuvat model-oliossa?**

Jos kirjan tiedot muuttuvat model-oliossa, tulee näkymän myös päivittyä. Modeliin voi lisätä tapahtumankuuntelijoita komennolla `bind`. Erilaisten tapahtumien lista löytyy osoitteesta <http://backbonejs.org/#FAQ-events>. Haluamme kuunnella `model`-oliossa tapahtuvia muutoksia. Aina kun olio muuttuu, tulee meidän näyttää näkymä uudestaan.

Aiemmassa `ListView`-versiossa näkymän näyttäminen tapahtui osana `initialize`-kutsua. Siirretään näkymän näyttäminen erilliselle `render`-metodille, ja lisätään `initialize`-kutsuun modelin muutosten kuuntelu. Komennolla `this.model.bind` liitämme tähän näkymään liittyvään malliin parametrina annetun tyyppisen tapahtuman kuuntelijan, joka kutsuu parametrina annettavaa metodia parametrina annetulta oliolta.


{% highlight js %}


library.view.ListView = Backbone.View.extend({

  el: $("#main"),

  initialize: function() {
      this.model.bind("change", this.render, this);
      this.render(); // näytetään näkymä olion luonnin yhteydessä
  },

  render: function() {
      var html = Mustache.render(
          $("#single-book-template").html(),
          this.model.toJSON()
      );
      $("#main").html(html);
  }

});

{% endhighlight %}

<small>Listaus 19.</small>


Näkymän päivittymistä voi testata lisäämällä automaattisen päivitysskriptin osaksi sivun latautumista. Javascriptin komento `setInterval` saa parametrina funktion ja luvun. Kun sitä kutsutaan, se alkaa kutsumaan parametria kerran luvun (millisekunteja) määräämässä ajassa. Alla päivitämme mallikirjan nimeä kerran viidessä sekunnissa.


{% highlight js %}

$(document).ready(function() {

  var book = new library.model.Book({
    name:"Harry Potter ja viisasten kivi",
    pages:"335",
    isbn:"951-31-1146-6"
  });

  new library.view.NavigationView({
    model: book
  });

  setInterval(function() {
    book.set("name", book.get("name") + " :)");
  }, 5000);

});

{% endhighlight %}

<small>Listaus 20.</small>

![Kirja](../img/weso-library-esim-paranee.png "Kirja"){: style="display: block; margin: auto; margin-top: 10px; width: 450px;"}

<small>Kuva 1. </small>


#### Kokoelmat

Kirjastosovelluksemme ei ole vielä mielekäs, sillä se sisältää vain yhden kirjan. Jotta kirjastomme sisältäisi useampia kirjoja, tulee käytössämme olla jonkinlainen kokoelma. Backbone tarjoaa kahdenlaisia malleja: Model kuvaa yksittäistä asiaa, ja [Collection][Collection] kuvaa joukkoa yksittäisiä asioita. Tehdään kokoelmakonstruktori BookList, joka sisältää kirjoja. Kokoelman sisältämä mallityyppi annetaan parametrilla `model`.

[Collection]: http://backbonejs.org/#Collection


{% highlight js %}

library.model.BookList = Backbone.Collection.extend({
  model: library.model.Book
});

{% endhighlight %}

<small>Listaus 21.</small>


Kokoelmaan voi lisätä uusia kirjoja `add`-metodilla. Lisätään seuraavaksi toiminnallisuus listan näyttämiseen. Muokataan ensin sivun lataustoiminnallisuutta siten, että navigaationäkymä saa parametrina `books`-kokoelman.


{% highlight js %}

$(document).ready(function() {

  var book = new library.model.Book({
    name:"Harry Potter ja viisasten kivi",
    pages:"335",
    isbn:"951-31-1146-6"
  });

  var books = new library.model.BookList();
  books.add(book);

  new library.view.NavigationView({
    model: books
  });

});

{% endhighlight %}

<small>Listaus 22.</small>


Muokataan tämän jälkeen listanäkymää. Lisätään ensin HTML-template, joka listaa kaikki kirjat. Jos kirjoja ei ole ollenkaan, näytetään viesti "No books :(".

{% highlight html %}
<script id="list-books-template" type="text/html">
{% endhighlight %}

{% highlight html %}
{% raw %}

  {{#list}}
      <p>
          <label for="name">Name</label>
          <span name="name">{{name}}</span><br/>
          <label for="pages">Pages</label>
          <span name="pages">{{pages}}</span><br/>
          <label for="isbn">ISBN</label>
          <span name="isbn">{{isbn}}</span>
      </p>
  {{/list}}

  {{^list}}
      <p>No books :(</p>
  {{/list}}

{% endraw %}
{% endhighlight %}

{% highlight html %}
</script>
{% endhighlight %}

<small>Listaus 23.</small>


Muokataan `ListView`-näkymää siten, että se käyttää tunnuksella `list-books-template` merkattua templatea. Koska käytämme Mustachea datan renderöintiin, luodaan dataa varten erillinen olio, jossa olevassa attribuutissa `list` kirjat ovat.


{% highlight js %}

library.view.ListView = Backbone.View.extend({

  // konteksti
  el: $("#main"),

  initialize: function() {
    this.model.bind("change", this.render, this);
    this.render();
  },

  render: function() {
    var data = {
        list: this.model.toJSON()
    };
    var html = Mustache.render($("#list-books-template").html(), data);
    $("#main").html(html);
  }        

});

{% endhighlight %}

<small>Listaus 24.</small>


Nyt näemme kirjat listana. Jos lisäämme sovellukseen aiemmin kokeilemamme `setInterval`-kutsun, huomaamme, että näkymä päivittyy vieläkin. Kokoelman sisällä tapahtuvat tapahtumat näkyvät siis myös kokoelman ulkopuolelle.

Muokataan seuraavaksi näkymää `AddView` siten, että lisää kirjan kokoelmaan. Kokoelmaan liittyvä `add` hoitaa myös datan validoinnin. Se heittää poikkeuksen jos näkymään lisättävässä datassa on virhe. Poikkeusten käsittely tapahtuu Javasta tutulla `try-catch`-syntaksilla. Lisätään `AddView`-näkymään toiminnallisuus, jossa käyttäjälle näytetään virhe jos lisääminen epäonnistuu. Jos lisääminen onnistuu, näytetään teksti "Kiitsä!".


{% highlight js %}

library.view.AddView = Backbone.View.extend({

  // ...
  save: function() {
    var data = this.serialize();
    try {
        this.model.add(data);
    } catch (err) {
        alert(err);
        return;
    }

    $("#main").html("<h2>Kiitsä!</h2>");
  }
// ...

{% endhighlight %}

<small>Listaus 25.</small>


Datan lisääminen kirjaoliona kokoelmaan onnistuu myös.


{% highlight js %}

library.view.AddView = Backbone.View.extend({

// ...
  save: function() {
    var data = this.serialize();
    try {
        this.model.add( new library.model.Book(data) );
    } catch (err) {
        alert(err);
        return;
    }

    $("#main").html("<h2>Kiitsä!</h2>");
  }
// ...


{% endhighlight %}

<small>Listaus 26.</small>


Huom! Tutki mitä tapahtuu kun yrität lisätä kirjaa, joka ei ole validi. Jos modelilla on validointi, ja validointi epäonnistuu, tulee uusi kirja olemaan tyhjä. Kokeile samaa myös seuraavalla koodilla, huomaatko toiminnallisuudessa mitään eroja?


{% highlight js %}

library.view.AddView = Backbone.View.extend({
  // ...
  save: function() {
    var data = this.serialize();
    var book = new library.model.Book(data);
    try {
        this.model.add( book );
    } catch (err) {
        alert(err);
        return;
    }
    $("#main").html("<h2>Kiitsä!</h2>");
  }
  // ...

{% endhighlight %}

<small>Listaus 26.</small>


Muokataan lopulta `AddView`-näkymän initialize-funktiota siten, että se poistaa alustusvaiheessa `click`-tapahtumankäsittelijän. Tämä estää sen, ettei samalla näkymällä ole useita klikkauksenkuuntelijoita.


{% highlight js %}

library.view.AddView = Backbone.View.extend({
  // ...
  initialize: function() {
      $("#main").unbind("click");
      $("#main").html($("#add-book-template").html());
  },
  // ...

{% endhighlight %}

<small>Listaus 27.</small>


#### Kommunikointi palvelimen kanssa

Backbone tarjoaa tuen myös palvelimen kanssa kommunikointiin. Jos Collection-oliolle lisätään attribuutti `url`, osaa backbone hakea dataa palvelimelta. Datan haku onnistuu esimerkiksi collection-oliolle liittyvällä `fetch` kutsulla, jolle voi antaa parametrina datan lisääminen kokoelmaan `{add : true}`. Luodaan kaksi konstruktoria. Toista käytetään model-olioiden luontiin, ja toista kokoelmien luontiin.


{% highlight js %}

site.model.Cool = Backbone.Model.extend({
  initialize: function() {
    this.save();
  }
});

site.model.Coollection = Backbone.Collection.extend({
  url: "http://rest-apin-osoite.com/cools",
  model: site.model.Cool
});

{% endhighlight %}

<small>Listaus 28.</small>


Kun luomme kokoelmaolion, ja kutsumme sen `fetch`-metodia, kokoelma hakee kaikki siihen liittyvät datat.


{% highlight js %}

var collection = new site.model.Coollection();
collection.fetch({ add: true });

{% endhighlight %}

<small>Listaus 29.</small>


Koska `model`-oliolla on `initialize`-funktiossa metodikutsu `save`, se tallennetaan automaattisesti kokoelmassa määriteltyyn osoitteeseen. Huom! Automaattinen tallennus onnistuu koska luomme uuden `Cool`-olion `Coollection`-olion kautta. Huomaa myös, että kun komento `fetch` lisää haettuja olioita kokoelmaan, lisäystapahtuman tyyppi on `add`. Jos haluat, että näkymässä tapahtuu muutos, niin kytkös tapahtumatyyppiin `change` ei siis riitä.</p>


{% highlight js %}

var collection = new site.model.Coollection();
collection.fetch({ add: true });

collection.add({coolness:42});

{% endhighlight %}

<small>Listaus 30.</small>


Backbone.js olettaa, että rajapinta on REST-tyylinen.


#### Reititys

*Backbone.js* tarjoaa myös historiatuen, jossa sivujen välillä tapahtuva navigointi tapahtuu ankkuritageja käyttäen. Ankkuritagien avulla yhden sivun saa kuuntelemaan esimerkiksi osoitetta `sivu.html#add` ja toisen sivun kuuntelemaan osoitetta `sivu.html#remove`. Tämä mahdollistaa sivujen lisäämisen kirjanmerkkeihin, sekä helpottaa esimerkiksi sivujen läpikäyntiä erilaisten crawlerien toimesta (ml. google).

Lisää reitittimistä löytyy osoitteesta <http://backbonejs.org/#Router>.

{% comment %}

<!--
TODO: tähän miksi ei jepa

http://www.w3.org/Provider/Style/URI.html
http://engineering.twitter.com/2012/05/improving-performance-on-twittercom.html
http://danwebb.net/2011/5/28/it-is-about-the-hashbangs
HTML5: pushstate https://developer.mozilla.org/en-US/docs/DOM/Manipulating_the_browser_history
   https://github.com/balupton/history.js
-->

{% endcomment %}



[^lisenssi]: <small>Tämä materiaali on lisensoitu Creative Commons BY-NC-SA-lisenssillä, joten voit käyttää ja levittää sitä vapaasti, kunhan alkuperäisten tekijöiden nimiä ei poisteta. Jos teet muutoksia materiaaliin ja haluat levittää muunneltua versiota, se täytyy lisensoida samanlaisella vapaalla lisenssillä. Materiaalien käyttö kaupalliseen tarkoitukseen on ilman erillistä lupaa kielletty.</small>

[^tekijat]: <small>Tämä materiaali on alunperin tarkoitettu Helsingin yliopiston tietojenkäsittelytieteen laitoksen syksyn 2012 kurssille web-selainohjelmointi. Materiaalin kirjoittaja on *Arto Vihavainen* ja sen syntyyn ovat vaikuttaneet useat tahot, joista tärkein on *Mikael Nousiainen*. Iso kiitos kuuluu myös *Kasper Hirvikoskelle*. </small>

<br/>
