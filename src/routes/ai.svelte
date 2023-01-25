<main>
	<h1>Uzdevums atvērto durvju dienai</h1>
	<p>
		Programmēšanas tehniķis spēj izveidot funkcionālu un modernu tīmekļa lapu. Tomēr tas nav viss!
		Programmētāji darbojas daudzās un dažādās jomās, no kurām viena ir arī mākslīgais intelekts
		(angļu v. Artificial intelligence). Lai gūtu ieskatu savā nākotnes profesijā, Tu tūlīt izveidosi
		tīmekļa vietni, kurā, izmantojot mākslīgo intelektu, tiks atpazīti attēlā esoši objekti.
	</p>
	<h2>Sagatavošanās darbam</h2>
	<ol>
		<li>
			Lejuplādē, lūdzu, 3 datnes jeb failus:
			<ul>
				<li><a href="ai-start/index.html" download="index.html">index.html</a></li>
				<li><a href="ai-start/script.js" download>script.js</a></li>
				<li><a href="ai-start/style.css" download>style.css</a></li>
			</ul>
		</li>
		<li>Mapē <em>Dokumenti</em> izveido mapi <em>ai</em></li>
		<li>Mapē <em>ai</em> pārvieto 3 lejuplādētās datnes.</li>
		<li>Atver šo mapi lietojumprogrammā <em>Visual Studio Code</em>.</li>
		<li>Atver, apskati katru no datnēm.</li>
	</ol>
	<p>Kaut arī pamatkods jau ir dots, Tev ir jāizlabo radušās kļūdas.</p>
	<h2>Lapas skelets <em>index.html</em></h2>
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
	<h2>Lapas izskats <em>style.css</em></h2>
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
	<h2>Lapas funkcionalitāte <em>script.js</em></h2>
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
	<h2>Lapas testēšana</h2>
	<p>
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
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,400;1,300&display=swap');

	main {
		font-family: 'Josefin Sans', sans-serif;
		max-width: 980px;
		margin: 80px auto;
	}

	@media (max-width: 980px) {
		main {
			margin: 80px 40px;
		}
	}
	h1 {
		font-size: 40px;
		text-align: center;
	}
	p,
	li {
		font-size: 18px;
		line-height: 1.5;
	}

	ul {
		margin-top: 7px;
		margin-bottom: 20px;
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
	}
</style>
