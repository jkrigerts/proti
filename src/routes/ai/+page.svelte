
<h1>Objektu atpazīšana attēlā</h1>

<article>
  <p>
    Programmēšanas tehniķis spēj izveidot funkcionālu un modernu tīmekļa lapu. Tomēr tas nav viss!
    Programmētāji darbojas daudzās un dažādās jomās, no kurām viena ir arī mākslīgais intelekts
    (angļu v. Artificial intelligence). Lai gūtu ieskatu savā nākotnes profesijā, Tu tūlīt izveidosi
    tīmekļa vietni, kurā, izmantojot mākslīgo intelektu, tiks atpazīti attēlā esoši objekti.
  </p>
</article>

<article>
  <h2>Projekta lejuplāde</h2>
  <ol>
    <li>
      Lejuplādē, lūdzu, 3 datnes jeb failus:
      <ul>
        <li><a href="ai-start/index.txt" download>index.txt</a></li>
        <li><a href="ai-start/script.js" download>script.js</a></li>
        <li><a href="ai-start/style.css" download>style.css</a></li>
      </ul>
    </li>
    <li>Datorā mapē <em>Dokumenti</em> izveido mapi <em>ai</em></li>
    <li>Mapē <em>ai</em> pārvieto 3 lejuplādētās datnes</li>
  </ol>
  <p>Kaut arī pamatkods jau ir dots, Tev būs jāizlabo radušās kļūdas!</p>
</article>

<article>
  <h2>Projekta atvēršana</h2>
  <p>Varētu jau dažādo programmēšanas valodu datnes atvērt un rediģēt jebkurā teksta apstrādes
    lietotnē, jā arī <em>Word</em> vai <em>Google Docs</em>, tomēr tas būtu gaužām neērti!
    Tieši tāpēc programmētājiem ir īpašas lietojumprogrammas, ko sauc par <strong>integrētajām izstrādes vidēm</strong>.
    Viena no tādām ir <em>Visual Studio Code</em>.
  </p>
  <ol>
    <li>Atver lietojumprogrammu <em>Visual Studio Code</em></li>
    <li>Izvēlies <em>File</em> -&gt; <em>Open Folder</em></li>
    <li>Atrdodi un atver mapi <em>ai</em>, kuru pats izveidoji</li>
    <li>Pārsauc datni <em>index.txt</em> par <em>index.html</em></li>
    <li>Apskati <em>index.html</em> saturu</li>

  </ol>
</article>

<article>
  <h2>Lokālais serveris</h2>
  <p>Lai parasts dators pārtaptu par tīmkeļa vietnes serveri, ir nepieciešams izmantot īpašas
    programmas, kas paredzētas šim nolūkam. 
  </p>
  <ol>
    <li><em>Visual Studio Code</em> kreisajā malā atrodi un atver sadaļu <em>Extensions</em></li>
    <li>Meklētājā ieraksti <em>Live Server</em> - tā ikona ir kā violets Wi-Fi raidītājs uz abām pusēm</li>
    <li>Ieinstalē šo paplašinājumu, izvēloties <em>Install</em></li>
    <li>Labajā apakšējā <em>Visual Studio Code</em> stūrī ieraudzīsi vārdus <em>Go Live</em>. Ja tos neredzi, aizver
    <em>Visual Studio Code</em> un atver no jauna</li>
    <li>Nospied <em>Go Live</em></li>
    <li>Ja tas neatveras automātiski, interneta pārlūkprogrammā,
      piemēram, <em>Google Chrome</em> ieraksti <em>http://localhost:5500</em></li>
  </ol>
  <p>Lokālais serveris ir palaists un esi gatavs programmēšanai!</p>
</article>


<article>
  <h2>Lapas skelets ar <em>HTML</em></h2>
  <ol>
    <li>
      Datnē <em>index.html</em> 11. rindiņā pirms vārda <code>Objekti</code> ieraksi
      <code>&lt;h1&gt;</code>
    </li>
    <li>
      Šajā paša datnē 18. rindiņā starp <code>&lt;button&gt;</code> un <code>&lt;/button&gt;</code>
      ieraksti tekstu <code>Atpazīt</code>
    </li>
  </ol>
</article>

<article>
  <h2>Lapas izskats ar <em>CSS</em></h2>
  <ol>
    <li>
      Datnē <em>index.html</em> 7. rindiņu aizstāj ar
      <code>&lt;link rel="stylesheet" href="style.css" /&gt;</code>
    </li>
    <li>
      Datnē <em>style.css</em> atrodi vārdu <code>visibility</code>. Aiz kola esošo vērtību
      <code>hidden</code>
      nomaini uz <code>visible</code>
    </li>
    <li>
      Datnē <em>style.css</em> atrodi vārdu <code>background-video</code> un nomaini to uz
      <code>background-image</code>
    </li>
  </ol>
</article>


<article>
  <h2>Lapas funkcionalitāte ar <em>JavaScript</em></h2>
  <ol>
    <li>
      Datnē <em>index.html</em> 8. rindiņu aizstāj ar
      <code>&lt;script src="script.js"&gt;&lt;/script&gt;</code>
    </li>
    <li>
      Datnē <em>script.js</em> 1. rindiņā vārdu <code>nepareizs</code> nomaini uz
      <code>classifier</code>
    </li>
  </ol>
</article>

<article class="pb-4">
  <h2>Lapas testēšana</h2>
  <p class="mb-1">
    Laiks pārbaudīt, vai lapa strādā! Laukā <em>Saite uz attēlu:</em> pa vienai pēc kārtas ieliec saites
    uz attēliem:
  </p>
  <ul>
    <li>
      <code class="try"
        >https://upload.wikimedia.org/wikipedia/commons/d/d2/Siberian_Husky_with_Blue_Eyes.jpg</code
      >
    </li>
    <li>
      <code class="try"
        >https://upload.wikimedia.org/wikipedia/commons/1/1d/Football_Pallo_valmiina-cropped.jpg</code
      >
    </li>
    <li>
      <code class="try"
        >https://images.unsplash.com/photo-1630717285906-29364ffacea0?w=735&q=80</code
      >
    </li>
    <li>
      <code class="try"
        >https://images.unsplash.com/photo-1497206365907-f5e630693df0?w=880&q=80</code
      >
    </li>
  </ul>
  <p>Vai mākslīgais intelekts pareizi atpazīst objektus attēlos? Cik pārliecināts tas ir?</p>
</article>





<style>
	h1 {
		font-size: 3.5rem;
		text-align: center;
		margin: 0 10px;
    color: var(--primary-color);
    padding: 50px 0;
	}

  @media (max-width: 600px) {
		h1 {
			font-size: 2.5rem;
		}
	}

	@media (max-width: 600px) {
		h1 {
			font-size: 2.5rem;
		}
	}

  article {
    margin: 20px;
  }


	p,
	li {
		font-size: 1.3rem;
		line-height: 1.7;
	}


	ul {
		margin-top: 7px;
		margin-bottom: 20px;
	}

  strong {
		font-weight: 900;
		font-family: Arial, Helvetica, sans-serif;
		color: #0c5eec;
	}

	em {
		font-weight: 700;
		font-family: Arial, Helvetica, sans-serif;
		color: #27b500;
	}
	h2 {
		margin-top: 70px;
		font-size: 26px;
	}

	code {
		font-weight: 700;
		font-family: Arial, Helvetica, sans-serif;
		color: #9800f0;
		word-break: break-all;
	}

	.try {
		font-weight: 300;
    font-size: 1rem;
	}

  .mb-1 {
    margin-bottom: 8px;
  }

  .pb-4 {
    padding-bottom: 24px;
  }
</style>
