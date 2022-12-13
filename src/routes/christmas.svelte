<script>
	import Snow from '../components/Snow.svelte';
</script>

<svelte:head
	><title>DG konkurss</title>
	<style>
		body {
			background: linear-gradient(to left, #031050, #0881d2);
		}
	</style>
</svelte:head>

<header><Snow /></header>
<main>
	<div class="head">
		<h1>Palīdzēsim Ziemassvētku vecītim kopā!</h1>
		<p class="lead"><em>Draugiem Group</em> konkurss</p>
	</div>
	<p>
		Tev ir divi lieli uzdevumi – aizmugursistēmā (angļu v. <em>back-end</em>) ir jāizveido 4
		<em>PHP</em>
		funkcijas, kuras iegūst datus no <em>MySQL</em> datubāzes, savukārt priekšgalsistēmā (angļu v.
		<em>front-end</em>) jāizveido reaģējoša tīmekļa vietne! Darba ir daudz, bet laiks – tikai 4
		astronomiskās stundas, tāpēc izvērtē kārtīgi, ko darīsi, bet ko iespējams izlaidīsi.
	</p>
	<article class="big">
		<h2>Datubāze</h2>
		<p>
			Ziemassvētku vecītis bērnu atsūtītās vēstules glabā <em>MySQL</em> datubāzē. Tomēr kurš katrs nevar
			saņemt dāvanas, tāpēc datubāzē tiek glabātas arī bērnu sekmes. Tā Ziemassvētku vecītis var izvērtēt,
			kurš ir bijis centīgs, bet kurš – ne tik ļoti.
		</p>
		<article>
			<h3>Piekļuve datubāzei</h3>
			<ul>
				<li>Datubāzes serveris (<em>host</em>): <strong>server43.areait.lv</strong></li>
				<li>Lietotājvārds: <strong>jekabsar_reader</strong></li>
				<li>Parole: <strong>Christmas2022</strong></li>
				<li>Datubāzes nosaukums: <strong>jekabsar_christmas</strong></li>
			</ul>
		</article>
		<article>
			<h3>Datubāzes uzbūve</h3>
			<div class="table-container">
				<article class="table">
					<h4>Tabula <code>children</code></h4>

					<table>
						<thead>
							<tr>
								<th>Kolonnas nosaukums</th>
								<th>Kolonnas apraksts</th>
							</tr>
						</thead>
						<tbody>
							<tr>
								<td><code>id</code></td>
								<td>Primārā atslēga</td>
							</tr>
							<tr>
								<td><code>firstname</code></td>
								<td>Vārds</td>
							</tr>
							<tr>
								<td><code>middlename</code></td>
								<td>Otrais vārds, ja ir</td>
							</tr>
							<tr>
								<td><code>surname</code></td>
								<td>Uzvārds</td>
							</tr>
							<tr>
								<td><code>age</code></td>
								<td>Vecums</td>
							</tr>
						</tbody>
					</table>
				</article>
				<article class="table">
					<h4>Tabula <code>gifts</code></h4>
					<table>
						<thead>
							<tr>
								<th>Kolonnas nosaukums</th>
								<th>Kolonnas apraksts</th>
							</tr>
						</thead>
						<tbody>
							<tr>
								<td><code>id</code></td>
								<td>Primārā atslēga</td>
							</tr>
							<tr>
								<td><code>name</code></td>
								<td>Dāvanas nosaukums</td>
							</tr>
							<tr>
								<td><code>count_available</code></td>
								<td>Pieejamais dāvanu skaits</td>
							</tr>
						</tbody>
					</table>
				</article>
				<article class="table">
					<h4>Tabula <code>grades</code></h4>
					<table>
						<thead>
							<tr>
								<th>Kolonnas nosaukums</th>
								<th>Kolonnas apraksts</th>
							</tr>
						</thead>
						<tbody>
							<tr>
								<td><code>id</code></td>
								<td>Primārā atslēga</td>
							</tr>
							<tr>
								<td><code>student_id</code></td>
								<td>Ārējā atslēga uz tabulu <code>children</code></td>
							</tr>
							<tr>
								<td><code>subject</code></td>
								<td>Mācību priekšmets</td>
							</tr>
							<tr>
								<td><code>grade</code></td>
								<td>1. semestra vērtējums ballēs</td>
							</tr>
						</tbody>
					</table>
				</article>
				<article class="table">
					<h4>Tabula <code>letters</code></h4>
					<table>
						<thead>
							<tr>
								<th>Kolonnas nosaukums</th>
								<th>Kolonnas apraksts</th>
							</tr>
						</thead>
						<tbody>
							<tr>
								<td><code>id</code></td>
								<td>Primārā atslēga</td>
							</tr>
							<tr>
								<td><code>sender_id</code></td>
								<td>Ārējā atslēga uz tabulu <code>children</code></td>
							</tr>
							<tr>
								<td><code>letter_text</code></td>
								<td>Vēstules teksts</td>
							</tr>
						</tbody>
					</table>
				</article>
			</div>
		</article>
	</article>
	<article class="big">
		<h2>Aizmugursistēma (<em>back-end</em>)</h2>
		<p>
			Šo uzdevumu pildi <em>skola.hex.lv</em>, ielogojoties ar savu lietotājvārdu un paroli.
			Vispirms jaunā failā (nosaukums nav būtisks) izveido savienojumu ar datubāzi, tad izpildi
			turpmāk prasīto! Kad uzdevums pabeigts, nokopē visu savu <em>PHP</em> kodu lokāli failā
			<code>back-end.php</code> (vairāk informācijas skatīt 5. punktā).
		</p>
		<article class="task">
			<h3>1. Funkcija <code>gifts_to_array($id)</code></h3>
			<p>
				Ir zināms, ka ikkatra atsūtītā vēstule beidzas ar tekstu <em class="important">dāvanas:</em
				>, pēc kā seko dāvanu saraksts, kuras sūtītājs vēlas saņemt svētkos. Tāpat ir zināms, ka
				katrs sūtītājs ir iesūtījis tikai vienu vēstuli. Tavs uzdevums ir izveidot funkciju
				<code>gifts_to_array($id)</code>, kura:
			</p>
			<ul>
				<li>
					saņem vienu argumentu – vēstules sūtītāja
					<em>id</em> (<code>sender_id</code>);
				</li>
				<li>atgriež masīvu ar dāvanām, kuras vēstules sūtītājs vēlas saņemt.</li>
			</ul>

			<p>Vari pārbaudīt, vai funkcija darbojas, kā nākas. Ja tavā kodā ieraksta rindiņu</p>
			<p><code class="blue">echo implode(", ", gifts_to_array(18));</code></p>
			<p>
				, tad
				<em>skola.hex.lv</em> konsolē parādās rezultāts:
			</p>
			<p><code class="green">kluči, lelle, ragavas, cimdi</code></p>
		</article>
		<article class="task">
			<h3>2. Funkcija <code>has_been_good($id)</code></h3>
			<p>
				Vēstuļu sūtītāji ir skolas vecuma bērni. Ikkatram no viņiem ir ne tikai Ziemassvētku vēlmes,
				bet arī šajā semestrī skolā saņemtās atzīmes. Ir uzskatāms, ka skolēns bijis centīgs bērns
				un saņems dāvanas, ja viņa vidējā atzīme ir 5 vai vairāk. Pretējā gadījumā dāvanas skolēns
				nesaņems<em class="red">*</em>. Tavs uzdevums ir izveidot funkciju
				<code>has_been_good($id)</code>, kura:
			</p>
			<ul>
				<li>
					saņem vienu argumentu – skolēna
					<em>id</em> (<code>student_id</code>);
				</li>
				<li>
					atgriež patiesumvērtību (<em>boolean</em>): <em>true</em>, ja skolēns ir nopelnījis
					dāvanas, turpretim <em>false</em>, ja dāvanas nepienākas.
				</li>
			</ul>

			<p>Vari pārbaudīt, vai funkcija darbojas, kā nākas. Ja tavā kodā ieraksta rindiņu</p>
			<p><code class="blue">echo has_been_good(19) ? "true" : "false";</code></p>
			<p>
				, tad
				<em>skola.hex.lv</em> konsolē parādās rezultāts:
			</p>
			<p><code class="green">true</code></p>
			<p class="red p-10-top">
				<em
					>* Šis ir vienkāršots uzdevums. Reālajā dzīvē tikai atzīmes vien nevar noteikt to, cik
					centīgs un labestīgs ir cilvēks.</em
				>
			</p>
		</article>
		<article class="task">
			<h3>3. Funkcija <code>summarize_children($offset, $count)</code></h3>
			<p>
				Lai Ziemassvētku vecīša darbu atvieglotu, datus par bērniem ir nepieciešams attēlot konsolē
				sakopotā veidā. Tavs uzdevums ir izveidot funkciju
				<code>summarize_children($offset, $count)</code>, kura:
			</p>
			<ul>
				<li>
					<p>saņem divus argumentus:</p>
					<ul>
						<li>
							<code>$offset</code> – bērni tiek sakārtoti alfabēta secībā pēc uzvārda un
							<code>$offset</code> norāda, no kura ieraksta pēc kārtas rādīt rezultātus konsolē (ja
							rādīt no paša pirmā ieraksta, tad <code>$offset = 0</code>),
						</li>
						<li>
							<code>$count</code> – cik ierakstus (bērnus, rindiņas) parādīt konsolē;
						</li>
					</ul>
				</li>
				<li>
					<p>
						<em>skola.hex.lv</em> konsolē izvada sarakstu, kur katrā rindiņā (rindiņas atdalīt var
						ar <code>echo "\n";</code>) redzams:
					</p>
					<ul>
						<li>bērna vārds (arī otrs vārds, ja tāds ir),</li>
						<li>bērna uzvārds,</li>
						<li>tas, vai bērns saņems dāvanas (jā vai nē),</li>
						<li>
							bērna atsūtītajā vēstulē minētais vēlamo dāvanu saraksts, kur dāvanas viena no otras
							atdalītas ar komatu.
						</li>
					</ul>
				</li>
			</ul>

			<p>Vari pārbaudīt, vai funkcija darbojas, kā nākas. Ja tavā kodā ieraksta rindiņu</p>
			<p><code class="blue">summarize_children(6, 3);</code></p>
			<p>
				, tad
				<em>skola.hex.lv</em> konsolē parādās rezultāts:
			</p>
			<p>
				<code class="green"
					>Ivanda Kandava. Saņems dāvanas? Jā! Vēlas: kluči, lelle, ragavas, cimdi</code
				>
			</p>
			<p>
				<code class="green">Marija Guna Kriščo. Saņems dāvanas? Jā! Vēlas: lego, kāmītis</code>
			</p>
			<p>
				<code class="green">Anna Liepiņa. Saņems dāvanas? Nē! Vēlas: kaķēns</code>
			</p>
		</article>
		<article class="task">
			<h3>4. Funkcija <code>not_enough()</code></h3>
			<p>
				Arī Ziemassvētku vecīša dāvanu krājumi ir ierobežoti, un var gadīties, ka dāvanu ir mazāk
				nekā nepieciešams. Ir zināms, ka katrs bērns vēlas tikai tādas dāvanas, kuras ir
				Ziemassvētku vecīša sarakstā (tabulā <em>gifts</em>), kā arī nav itin nevienas kļūdas dāvanu
				nosaukumos, kurus bērni minējuši savās vēstulēs. Ja bērns atzīmju dēļ dāvanas nesaņems, tad
				viņa vēlmes nav jāņem vērā (dāvanas nav jāskaita). Tavs uzdevums ir izveidot funkciju
				<code>not_enough()</code>, kura:
			</p>
			<ul>
				<li>nesaņem nevienu argumentu;</li>
				<li>
					<em>skola.hex.lv</em> konsolē izvada tās dāvanas, kuras vēl trūkst, kā arī skaitu, cik
					šādas dāvanas vēl nepieciešams sagatavot pirms svētkiem (katra dāvana jaunā rindiņā,
					rindiņas var atdalīt ar <code>\n</code>).
				</li>
			</ul>

			<p>Vari pārbaudīt, vai funkcija darbojas, kā nākas. Ja tavā kodā ieraksta rindiņu</p>
			<p><code class="blue">not_enough();</code></p>
			<p>
				, tad
				<em>skola.hex.lv</em> konsolē parādās <strong>vairākas</strong> rindiņas (neatklāšu, cik), no
				kurām divas ir:
			</p>
			<p><code class="green">Skandas => trūkst 1</code></p>
			<p><code class="green">Ragavas => trūkst 2</code></p>
		</article>
		<article class="task">
			<h3>5. Koda sagatavošana iesniegšanai</h3>
			<p>
				Tas arī aizmugursistēmai viss! Savu izveidoto <em>PHP</em> kodu gan neatstāj
				<em>skola.hex.lv</em>, bet izpildi turpmāk aprakstīto, citādi kods netiks ņemts vērā.
			</p>
			<ol>
				<li>Mapē <code>Documents</code> izveido apakšmapi <code>christmas</code>.</li>
				<li>Atver mapi <code>christmas</code> ar IDE <em>Visual Studio Code</em>.</li>
				<li>Izveido failu <code>back-end.php</code>.</li>
				<li>Pārkopē visu savu kodu no <em>skola.hex.lv</em> uz failu <code>back-end.php</code>.</li>
				<li>
					Saglabā izmaiņas, vēlāk, pašās darba beigās mapi <code>christmas</code> saarhivētā formātā
					tu iesūtīsi <em>Skolo.lv</em>.
				</li>
			</ol>
		</article>
	</article>
	<article class="big">
		<h2>Priekšgalsistēma (<em>front-end</em>)</h2>
		<p>
			Ziemassvētku vecītis, lai atvieglotu savu darbu, ir nolēmis izveidot tīmekļa vietni <em
				>Vēstule Ziemassvētku vecītim</em
			>. Paredzēts, ka tajā ikviens var nosūtīt Ziemassvētku vecītim vēstuli ar vēlmju sarakstu,
			izpildot 3 vienkāršus soļus. Un nu pati labākā daļa – šīs vietnes izveidi Ziemassvētku vecītis
			ir uzticējis tieši tev!
		</p>
		<article>
			<h3>Prasības</h3>
			<ul>
				<li>
					Fonts visam tekstam: <a
						href="https://fonts.google.com/specimen/Josefin+Sans?query=josefin+sans"
						target="_blank"
					>
						<strong>Josefin Sans</strong></a
					>.
				</li>
				<li>
					Izmantojamās krāsas:
					<ul>
						<li>#165b33</li>
						<li>#146b3a</li>
						<li>#f8b229</li>
						<li>#ea4630</li>
						<li>#bb2528</li>
						<li>melna, balta un pelēka pēc izvēles.</li>
					</ul>
				</li>
				<li>
					Lapai ir jābūt reaģējošai (angļu v. <em>responsive</em>) – tai labi jāizskatās kā uz
					<em>iPhone SE</em> ekrāna, tā arī uz <em>MacBook Air 13''</em> ekrāna.
				</li>
				<li>Pēc iespējas jāizmanto <em>HTML Semantic Elements</em>.</li>
				<li>
					Jāseko labajai praksei – jaātdala HTML, CSS, JavaScript, nevajadzētu lietot <em
						>inline styles</em
					>, CSS atslēgvārdu <code>!important</code> u.c.
				</li>
				<li>
					<p>Kad tiek nospiesta poga <em><strong>Sūtīt!</strong></em>, konsolē parādās:</p>
					<p><code class="green">Vārds: [lapas lietotāja ierakstītais vārds]</code></p>
					<p><code class="green">Uzvārds: [lapas lietotāja ierakstītais uzvārds]</code></p>
					<p>
						<code class="green">Vēstules teksts: [lapas lietotāja ievadītais vēstules teksts]</code>
					</p>
					<p>
						<code class="green"
							>Izvēlētās dāvanas: [lapas lietotāja izvēlēto dāvanu nosaukumi, atdalīti ar komatu]</code
						>
					</p>
				</li>
				<li>Zemāk ir dots video, kurā redzams, kā jāizskatās gala vietnei.</li>
			</ul>
		</article>
		<article>
			<h3>Paraugs</h3>
			<div class="center-wrapper">
				<iframe
					width="760"
					height="485"
					src="https://www.youtube.com/embed/cvNJmBXDWxs"
					title="Paraugs"
					frameborder="0"
					allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
					allowfullscreen
				/>
			</div>
		</article>
		<article>
			<h3>Resursi</h3>
			<p>Šeit vari iegūt nepieciešamos attēlus. Spied ar labo peles pogu un lejuplādē!</p>
			<div class="container">
				<img src="/images/book.jpg" alt="Book" class="" />
				<div><img src="/images/1write.svg" alt="Write" class="sm" /></div>
				<img src="/images/ball.jpg" alt="Ball" class="" />
				<div><img src="/images/2choose.svg" alt="Choose" class="sm" /></div>

				<img src="/images/lego.jpg" alt="Lego" class="" />
				<img src="/images/robot.jpg" alt="Robot" class="" />

				<img src="/images/sled.jpg" alt="Sled" class="" />
				<img src="/images/toy.jpg" alt="Toy" class="" />

				<div><img src="/images/3send.svg" alt="Send" class="sm" /></div>
			</div>
		</article>
	</article>
	<article class="big">
		<h2>Darba iesniegšana</h2>
		<p>
			Lūdzu, visus failus – <code>back-end.php</code>, HTML, CSS, JavaScript, attēlus – saarhivē
			vienā
			<em>.zip</em>
			arhīvā un iesniedz <em>Skolo.lv</em> uzdevumā
			<a href="https://skolo.lv/mod/assign/view.php?id=65972354" target="_blank"
				><em>Draugiem Group konkurss</em></a
			>.
		</p>
	</article>
	<article class="big">
		<h2>Vērtēšanas kritēriji</h2>
		<p>
			Kopā par darbu var iegūt 88 punktus: 40 par aizmugursistēmu, 48 par priekšgalsistēmu.
			Detalizētu vērtēšanas kritēriju apskatu vari atrast <a
				href="vertesanas-kriteriji.pdf"
				target="_blank">šeit</a
			>
			vai arī <em>Skolo.lv</em> uzdevumā
			<a href="https://skolo.lv/mod/assign/view.php?id=65972354" target="_blank"
				><em>Draugiem Group konkurss</em></a
			>
		</p>
	</article>
</main>

<style>
	* {
		box-sizing: border-box;
	}
	:root {
		font-family: Arial, Helvetica, sans-serif;
		font-size: 20px;
	}

	/* :global(body) {
		background: linear-gradient(to left, #031050, #0881d2);
	} */
	main {
		max-width: 1080px;
		margin: 0 auto;
		background-color: whitesmoke;
		padding: 0 30px;
	}

	.head {
		padding: 50px;
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
	}
	h1 {
		font-size: 3rem;
		font-weight: 400;
		margin-bottom: 0;
	}

	.lead {
		font-size: 1.2rem;
		font-weight: 200;
		color: #ce6e07;
	}

	p {
		margin: 0;
	}

	.big {
		padding: 50px 0;
		padding-bottom: 100px;
	}

	ul {
		margin-top: 10px;
	}

	ul ul {
		margin-top: 0;
	}

	.blue {
		color: #031050;
		font-weight: 600;
	}

	.green {
		color: #165003;
		font-weight: 600;
	}

	.red {
		color: #ce6e07;
	}

	.p-10-top {
		padding-top: 20px;
	}

	article > ul > li {
		margin-bottom: 10px;
	}

	.task {
		margin-top: 80px;
	}

	article > article {
		margin-top: 50px;
	}

	.container {
		margin-top: 20px;
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
		justify-content: center;
	}

	.container div {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 270px;
	}

	img {
		width: 270px;
	}

	.sm {
		width: 100px;
	}

	h2 {
		font-size: 2rem;
	}

	.table-container {
		display: flex;
		gap: 40px;
		flex-wrap: wrap;
		justify-content: flex-start;
	}

	table,
	th,
	td {
		border: 1px solid black;
		border-collapse: collapse;
	}

	th,
	td {
		padding: 5px;
		font-size: 0.9rem;
	}

	h4 {
		margin: 3px;
	}

	iframe {
		max-width: 100%;
		max-height: 50vh;
	}

	.center-wrapper {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	header {
		display: flex;
		align-items: center;
		justify-content: flex-end;
		padding: 0 40px;
		height: 50px;
		width: 100%;
		background-color: rgba(245, 245, 245, 0.827);
		-webkit-backdrop-filter: blur(4px);
		backdrop-filter: blur(4px);
		position: fixed;
		top: 0;
		left: 0;
	}
</style>
