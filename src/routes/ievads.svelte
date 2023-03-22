<svelte:head
	><title>Ievads programmēšanā</title>
	<style>
		body {
			background: linear-gradient(to left, #031050, #0881d2);
		}
	</style>
</svelte:head>

<main>
	<div class="heading">
		<img src="images/rene.png" alt="Rene" />
		<h1>Ievads programmēšanā</h1>
		<p>Kopā ar Rene</p>
	</div>
	<p>Sako, lūdzu, uzdevuma punktiem, un palīdzi Rene darbā!</p>
	<article class="first-article">
		<h2>Sagatavošanās</h2>

		<ol>
			<li>
				Lejuplādē arhīvu <a href="rene.zip" download>rene.zip</a>
			</li>
			<li>
				Izvelc no ZIP arhīva visas datnes atsevišķā mapē datorā, kurai dod nosaukumu <code
					>rene</code
				>.
			</li>
			<li>Atver mapi <code>rene</code> iekš <em>Visual Studio Code</em>.</li>
			<li>Ielādē <em>Visual Studio Code</em> paplašinājumu <em>Live Server</em>.</li>
			<li>
				Atver datni <code>index.html</code>. Kad tā atvērta nospied labajā apakšējā stūrī
				<em>Go Live</em>.
			</li>

			<li>
				Atver datni <code>script.js</code> -
				<strong>tur Tu veiksi visas turpmākās izmaiņas</strong>.
			</li>
		</ol>
	</article>
	<article>
		<h2>Rene darbā - 1. istaba</h2>
		<ol>
			<li>
				Pirmā darba telpa <code>inWorkroom1</code> jau ir importēta, kā redzi 1. rindiņā. Tā ir arī
				uzbūvēta ar <code>inWorkroom1();</code>, kā redzi 4. rindiņā.
			</li>
			<li>
				Importēta arī ir Rene iespēja pakustēties vienu lauciņu uz priekšu <code>move</code>, kā
				redzi 2. rindiņā.
			</li>
			<li>
				Pasaki, lai Rene pārvietojas vienu soli.
				<ol class="small-ol">
					<li>Aiz 4. rindiņas nospied <strong>Enter</strong>.</li>
					<li>Ieraksti komandu <code>await&nbsp;move();</code></li>
				</ol>
				<p class="info">
					Lai kaut ko izdarītu, ir vajadzīgs laiks. Vārdiņš <code>await</code> pasaka, ka ir jāsagaida,
					kamēr Rene pakustās!
				</p>
			</li>
			<li>
				Cik reizes Rene vēl ir jāpaiet uz priekšu, lai tiktu pie kastes? Tik reizes izsauc komandu <code
					>await&nbsp;move();</code
				> - katru jaunā rindiņā!
			</li>
			<li>
				Laiks pateikt Rene, lai paņem kasti!
				<ol>
					<li>
						Koda 2. rindiņā aiz vārda <code>move</code> ieliec komatu, tad atstarpi un ieraksti
						<code>pickUp</code>.
					</li>
					<li>
						Aiz izsauktajām komandām
						<code>move</code> jaunā rindiņā ieraksti komandu <code>await&nbsp;pickUp();</code>
					</li>
				</ol>
			</li>
		</ol>
	</article>
	<article>
		<h2>Rene darbā - 2. istaba</h2>
		<ol>
			<li>Koda 1. rindiņā tekstu <code>inWorkroom1</code> izlabo uz <code>inWorkroom2</code></li>
			<li>
				Koda 4. rindiņā komandu <code>inWorkroom1()</code> nomaini uz
				<code>inWorkroom2()</code>. Re, Rene ir citā telpā!
			</li>
			<li>
				Lai tiktu līdz mērķim, Tev vajadzēs pateikt, lai Rene pagriežas!
				<ol>
					<li>
						Koda 2. rindiņā aiz <code>pickUp</code> liec komatu, tad atstarpi un importē funkciju
						<code>turnRight</code>.
					</li>
					<li>Kad vajadzīgs, kodā vari rakstīt <code>await&nbsp;turnRight();</code></li>
				</ol>
			</li>
			<li>
				Ņem vērā, ka Rene māk pagriezties tikai uz labo pusi! Saraksti kodu tā, lai Rene paņem
				kasti.
			</li>
		</ol>


	</article>
	<article>
		<h2>Iemāci Rene griezties pa kreisi</h2>
		<p>
			Vai nav nogurdinoši, ka Rene māk griezties tikai uz labo pusi? Kā panākt, lai tas pagriežas pa
			kreisi?
		</p>
		<p>
			Tu vari mācīt Rene jaunas kustības, veidojot savas funkcijas! Koda beigās izveido savu
			funkciju:
		</p>
		<div class="long-code">
			<p><code>async function turnLeft() &lbrace;</code></p>
			<p class="pl-20">
				Te saraksti <code>await&nbsp;turnRight();</code> tik reizes, cik vajadzīgs!
			</p>
			<p><code>&rbrace;;</code></p>
		</div>
		<p>Turpmāk kodā vari izsaukt jauno funkciju, rakstot <code>await&nbsp;turnLeft();</code></p>
	</article>

	<article>
		<h2>Rene ātrums</h2>
		<p>Vai zināji, ka vari likt Rene strādāt ātrāk vai lēnāk?</p>
		<ol>
			<li>Koda 2. rindiņā importē funkciju <code>setSpeed</code></li>
			<li>Nākošajā rindiņā aiz <code>inWorkroom2();</code> izsauc <code>setSpeed(3);</code></li>
			<li>
				Pamēģini mainīt skaitli <code>3</code> uz citām vērtībām, piemēram, <code>10</code> vai
				<code>0.5</code>!
			</li>
		</ol>
	</article>

	<article>
		<h2>Rene darbā - 3. istaba</h2>
		<ol>
			<li>
				<code>inWorkroom2</code> gan importā, gan funkcijas izsaukumā nomaini uz
				<code>inWorkroom3</code>.
				<p>Re, tagad Rene kaste ne tikai jāsavāc, bet arī jānoliek mērķī!</p>
			</li>
			<li>Importē funkciju <code>putDown</code></li>
			<li>Liec Rene savākt kasti.</li>
			<li>Liec Renē aiziet līdz mērķim.</li>
			<li>Noliec kasti, izsaucot komandu <code>await&nbsp;putDown();</code></li>
		</ol>
		<p>Vai kaste ir vietā? 🙂</p>
	</article>

	<article>
		<h2>Rene darbā - 4. istaba</h2>
		<ol>
			<li>
				<code>inWorkroom3</code> gan importā, gan funkcijas izsaukumā nomaini uz
				<code>inWorkroom4</code>.
				<p>Šajā istabā ir parādījušies šķēršļi - pelēkās rūtiņas</p>
			</li>
			<li>Izvairoties no šķēršļiem, nogādā kasti mērķī!</li>
		</ol>
	</article>

	<article>
		<h2>Rene darbā - 5. istaba</h2>
		<ol>
			<li>
				<code>inWorkroom4</code> gan importā, gan funkcijas izsaukumā nomaini uz
				<code>inWorkroom5</code>.
				<p>
					Šis izskatās pēc gara skrējiena! Vai vēlies atvieglot sev dzīvi? Programmēšanā viss ir
					iespējams!
				</p>
				<div class="info">
					<p>
						Programmēšanā eksistē cikli (angļu valodā <strong>loop</strong>) - uzraksti kodu
						vienreiz, bet dators darbības izpilda daudzas reizes. Arī Tu vari uzrakstīt ciklu, ko
						pildīs Rene!
					</p>
					<p>
						Zemāk dots cikls, kurš liks Rene paiet uz priekšu par tieši <span style="color: purple"
							>3</span
						> soļiem:
					</p>
					<div class="long-code">
						<p>
							for (let i = <span style="font-family: sans-serif">0</span>; i &#60;
							<span style="color: purple">3</span>; i++) &lbrace;
						</p>
						<p class="pl-20">await move();</p>
						<p>}&rbrace;;</p>
					</div>
					<p>
						Ja Tu <span style="color: purple">3</span> nomainīsi uz citu veselu skaitli, tad Renē pārvietoties
						tieši tik reizes, cik būsi norādījis.
					</p>
				</div>
			</li>
			<li>Izvairoties no šķēršļiem, nogādā kasti mērķī!</li>
		</ol>
	</article>

	<article>
		<h2>Rene darbā - 6. istaba</h2>
		<p>Noteikumi tie paši, tikai, uh! Kas par lielu istabu!</p>
	</article>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,400;1,300&display=swap');

	* {
		box-sizing: border-box;
	}

	main {
		font-size: 16px;
		font-family: 'Josefin Sans', sans-serif;
		max-width: 1080px;
		margin: 0 auto;
		background-color: whitesmoke;
		padding: 0 30px;
		padding-bottom: 20px;
	}

	@media (max-width: 1090px) {
		main {
			margin: 5px;
		}
	}

	@media (max-width: 700px) {
		main {
			padding: 0 10px 30px 10px;
		}
	}

	.heading {
		display: grid;
		width: 100%;
		position: relative;
		padding-top: 20px;
		grid-template-columns: minmax(min-content, max-content);
		justify-content: center;
		--rene-far-right: 89%;
		--rene-far-left: 5px;
	}

	h1 {
		font-size: 3rem;
		text-align: center;
		margin: 0;
	}

	.heading > p {
		text-align: center;
		font-size: 2rem;
		margin-top: 0;
		color: #555;
	}

	@media (max-width: 600px) {
		h1 {
			font-size: 2.5rem;
		}
		.heading > p {
			font-size: 1.8rem;
		}
	}

	@media (max-width: 600px) {
		h1 {
			font-size: 2.5rem;
		}
		.heading > p {
			font-size: 1.8rem;
		}
	}

	.heading > img {
		height: 70px;
		position: relative;
		top: 18px;
		left: 0;
		animation-name: rool;
		animation-duration: 20s;
		animation-iteration-count: infinite;
	}

	@media (max-width: 510px) {
		.heading {
			--rene-far-right: 73%;
			--rene-far-left: 8%;
		}
	}

	@keyframes rool {
		0% {
			left: var(--rene-far-left);
		}
		49% {
			transform: scaleX(1);
		}
		50% {
			left: var(--rene-far-right);
			transform: scaleX(-1);
		}
		99% {
			transform: scaleX(-1);
		}
		100% {
			transform: scaleX(1);
			left: var(--rene-far-left);
		}
	}

	@media (max-width: 510px) {
		.heading > img {
			top: 66px;
		}
	}

	p,
	ol {
		font-size: 1.3rem;
	}

	code {
		color: blueviolet;
	}

	em {
		font-weight: 900;
		color: rgb(0, 124, 128);
	}

	li {
		margin-top: 1rem;
	}

	article {
		margin-top: 20vh;
	}

	.first-article {
		margin-top: 10vh;
	}

	.small-ol > li {
		margin-top: 0.5rem;
	}

	.info {
		background-color: rgb(210, 243, 250);
		padding: 10px;
		margin: 10px 0;
		color: #222;
		font-size: 1.2rem;
		margin-left: -40px;
	}

	.long-code {
		background-color: rgb(250, 247, 210);
		padding: 10px;
	}

	.long-code > p {
		margin: 0;
		font-size: 1.2rem;
	}

	.pl-20 {
		padding-left: 2rem;
	}
</style>
