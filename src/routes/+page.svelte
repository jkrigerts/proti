<script>
  import { onMount } from 'svelte';

  import Code from "./Code.svelte";
  import Result from "./Result.svelte";
  import Congratulations from './Congratulations.svelte';

  let globalScore = 0;
  let totalScore = 1;
  let customCommands = {"pārvietot": ["ņemt();", "iet();", "likt();"]};

  const handleScore = () => {
    globalScore++;
  }

  const handleCustomCommands = (newCommandName, newCommandSequence) => {
    customCommands[newCommandName] = newCommandSequence;
    localStorage.setItem("custom-commands", JSON.stringify(customCommands));
  }

  const reset = () => {
    globalScore = 0;
    localStorage.clear();
    window.location.reload();
  }

  onMount(() => {
    const localStorageCustomCommands = localStorage.getItem("custom-commands");
    if (localStorageCustomCommands) {
      customCommands = JSON.parse(localStorage.getItem("custom-commands"));
    } else {
      localStorage.setItem("custom-commands", JSON.stringify(customCommands));
    };
  })
</script>

<svelte:head>
  <title>Ievads programmēšanā</title>
</svelte:head>

<Result globalScore={globalScore} totalScore={totalScore} reset={reset}/>
{#if globalScore == totalScore}
  <Congratulations/>
{/if}

<section class="heading">
  <img src="/rene.png" alt="Rene" />
  <h1>Ievads programmēšanā</h1>
  <p>Kopā ar VTDT robotu Rene</p>
</section>
<section>
  <article class="first-article">
    <div class="left">
      <p>Suņuks spēj iemācīties apsēsties, kad pasaki <code>Sēdi!</code>,
        un apgulties, kad pasaki <code>Guli!</code>. Tās ir komandas, instrukcijas,
        ko suņuks ir iegaumējis un atpazīst. Tomēr vienā brīdī draugs sagurst,
        savukārt tu apsēdies pie datora...
      </p>
      <p>
        Vai zināji, ka arī tagad tu vari turpināt uzdot dažādas komandas, tikai nu jau datoram?
        Instrukciju došanu datoram vai robotam, lai tas izpilītu dažādus uzdevumus,
        sauc par <em>programmēšanu</em> 🙂.
      </p>
      <p>Seko uzdevumiem un iegūsti ieskatu programmēšanā, kopā ar VTDT robotu Rene!</p>
    </div>
    <div class="right">
      <img src="dog.webp" alt="Suns" />
    </div>
  </article>
  <article>
    <h2><span>1. istaba.</span> Kastes savākšana</h2>
    <p class="mb-40">Aizvirzi Rene līdz kastei un palūdz to savākt.</p>
    <ol>
      <li>Lai Rene pakustētos vienu lauciņu uz priekšu, tev:
        <ol>
          <li>tumšā lauciņa 1. rindiņā jāievada komandu <code>iet();</code></li>
          <li>jānospiež pogu <em>Izpildīt</em>.</li>
          <li>mirkli jāuzgaida, jo ikkatrai darbībai ir vajadzīgs laiks.</li>
        </ol>
      </li>
      <li>Katru komandu rakstot jaunā rindiņā, aizvirzi Rene līdz tai rūtiņai, kur ir kaste.</li>
      <li>Lai Rene kasti savāktu, tev jāizsauc komandu <code>ņemt();</code></li>
      <li>Kad uzdevumu būsi veiksmīgi izpildījis, baltā poga <em>Izpildīt</em> pārtaps zaļā pogā <em>Izpildīts</em>.</li>
    </ol>
    <Code reneInit={[0, 2, 0]} boxInit={[3, 2]} no={1} aim={"box"} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>

  <article>
    <h2><span>2. istaba.</span> Kaste mērķī</h2>
    <p class="mb-40">Palīdzi Rene kasti nogādāt mērķī.</p>
    <ol>
      <li>Liec, lai Rene aiziet līdz kastei un savāc to kā iepriekš.</li>
      <li>Aizvirsi Rene līdz mērķim.</li>
      <li>Liec Rene nolikt kasti, izsaucot komandu <code>likt();</code></li>
    </ol>
    <Code reneInit={[0, 1, 0]} boxInit={[2, 1]} targetInit={[3, 1]} no={2} aim={"target"} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>

  <article>
    <h2><span>3. istaba.</span> Pagriezties</h2>
    <p class="mb-40">Palīdzi Rene kasti nogādāt mērķī.</p>
    <p>Uzdevuma noteikumi tie paši, kas iepriekš. Tikai šoriez īstājā brīdī liec, lai Rene pagriežas, izsaucot komandu <code>paLabi();</code></p>
    <Code reneInit={[1, 0, 0]} boxInit={[2, 2]} targetInit={[2, 3]} no={3} aim={"target"} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>

  <article>
    <h2><span>4. istaba.</span> Prasmju trūkums</h2>
    <p class="mb-40">Palīdzi Rene kasti nogādāt mērķī.</p>
    <p>Kaste atkal jānogādā mērķī, bet, ak vai! Rene nemāk griezties pa kreisi... Tomēr vai vari iziet šo istabu, izmantojot komandu <code>paLabi();</code>?</p>
    <Code reneInit={[0, 2, 0]} boxInit={[2, 2]} targetInit={[2, 0]} no={4} aim={"target"} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>

  <article>
    <h2><span>5. istaba.</span> Apmāci Rene!</h2>
    <p class="mb-40">Iemāci, lūdzu, Rene komandu <code>paKreisi();</code></p>
    <ol>
      <li>Lai Rene iemācītu jaunu komandu:
        <ol>
          <li>rindiņa jāsāk ar <code>prast</code></li>
          <li>tad jāliek tukšuma rakstzīme,</li>
          <li>tad jāuzraksta komandas nosaukums <code>paKreisi</code>, kurš jāpabeidz ar <code>()</code></li>
          <li>jāliek tukšuma rakstzīme,</li>
          <li>rindiņa jānoslēdz ar atverošo figūriekavu <code>&#123;</code></li>
        </ol>
      </li>
      <li>Nākošajā rindiņā jāliek 2 tukšuma rakstzīmes un jāizsauc tāda komanda, kuru Rene jau zina.</li>
      <li>Katrā tālākā rindiņā var izsaukt vēl Rene zināmās komandas.</li>
      <li>Kad prasme izveidota, pēdējā rindiņa jānoslēdz ar aizverošo figūriekavu <code>&#125</code></li>
    </ol>
    <p>Lūk, arī vienas jaunas prasmes <code>pārvietot();</code> piemērs, kuru es jau iemācīju Rene:</p>
    <div class="long-code">
			<p><code>prast pārvietot() &lbrace;</code></p>
			<p class="pl-20"><code>ņemt();</code></p>
			<p class="pl-20"><code>iet();</code></p>
			<p class="pl-20"><code>likt();</code></p>
			<p><code>&rbrace;;</code></p>
		</div>
    <p>Visos nākošajos uzdevumos vari izmantot tikko izveidotās prasmes <code>paKreisi();</code> un <code>pārvietot();</code></p>
    <Code reneInit={[1, 1, 0]} no={5} aim={"turnLeft"} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>

  <article>
    <h2><span>6. istaba.</span> Ātrums</h2>
    <p class="mb-40">Palīdzi Rene kļūt veiklākam.</p>
    <p>Ak vai, cik ilgi būs jāgaida, līdz Rene izpildīs visas komandas šajā istabā... Nesatraucies - tu vari
      likt Rene kustēties ātrāk! Pirms visām pārējām komandām, izsauc komandu <code>ātrums(10);</code></p>

      <ul>
        <li>Sākuma Rene ātrums ir 1.</li>
        <li>Ja vēlies,
        vari Rene likt kustēties lēnāk, apaļajās iekavās rakstos skaitli, kas mazāks par 1, piemēram, <code>ātrums(0,5);</code></li>
        <li>Vari likt Rene kustēties arī pavisam ātri, izsaucot komandu <code>ātrums(50);</code></li>
        <li>Vari pamēģināt iekavās ierakstīt pat vēl lielāku vai mazāku skaitli!</li>
        <li>Komandu <code>ātrums(10);</code> var izsaukt tik bieži, cik vēlies.</li>
      </ul>
      <div class="info mb-40">
        <p>Komandu <code>ātrums(22);</code> nav iespējams izmantot, kad tiek veidota jauna prasme ar <code>prast</code>.</p>
      </div>
    <Code reneInit={[0, 0, 0]} boxInit={[3, 0]} targetInit={[3, 3]} no={6} aim={"target"} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>


  <article>
    <h2><span>7. istaba.</span> Reizes</h2>
    <p class="mb-40">Saīsini savu uzrakstīto kodu!</p>
    <p>Kaut arī iepriekšējā istabā Rene kustas ātrāk, kods tik un tā ir garšs. To ir iespējams saīsināt,
      izmantojot atkārtoto darbību komandu:</p>
      <ol>
        <li>jaunu rindiņu sāc ar <code>reizes</code></li>
        <li>tad ieliec tukšuma rakstzīmi,</li>
        <li>turpini ar skaitli - cik reizes komandu Rene jāizpilda,</li>
        <li>visbeidzot uzraksti pašas komandas nosaukumu, noslēdzot to ar <code>();</code></li>
      </ol>

      <p>Piemēram, komanda <code>reizes 3 iet();</code> Rene liks pārvietoties 3 lauciņus uz priekšu.</p>

      <div class="info mb-40">
        <p>Komandu <code>reizes</code> nav iespējams izmantot, kad tiek veidota jauna prasme ar <code>prast</code>.</p>
        <p>Komandā <code>reizes</code> nav iespējams mainīt ātrumu ar <code>ātrums(10);</code>.</p>
      </div>
    <Code reneInit={[0, 0, 0]} boxInit={[3, 0]} targetInit={[3, 3]} no={7} aim={"target"} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>

  <article>
    <h2><span>8. istaba.</span> Šķēršļi</h2>
    <p class="mb-40">Apejot šķēršļus, nogādā kasti mērķī.</p>
    <p>Ops! Istabā ir uzradušies šķēršļi! Tie ir jāapiet, lai Rene izdzīvotu.</p>
    <Code reneInit={[0, 1, 0]} boxInit={[2, 3]} targetInit={[2, 0]} no={8} aim={"target"} obstacles={[[1, 0], [1, 1], [1, 3], [2,1]]} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>

  <article>
    <h2><span>9. istaba.</span> Lielā istaba</h2>
    <p class="mb-40">Veiksmi! 🙂</p>
    <Code rows={6} columns={6} reneInit={[0, 4, 0]} boxInit={[5, 0]} targetInit={[0, 5]} no={9} aim={"target"} obstacles={[[1, 1], [1, 2], [1, 3], [1, 4], [1, 5], [3, 1], [3, 2], [3, 3], [3, 4], [3, 0], [4, 4], [5, 2], [4, 0]]} handleScore={handleScore} customCommands={customCommands} handleCustomCommands={handleCustomCommands}/>
  </article>
  

</section>


<style>
  .heading {
		display: grid;
		width: 100%;
		position: relative;
		padding-top: 40px;
		grid-template-columns: minmax(min-content, max-content);
		justify-content: center;
		--rene-far-right: 89%;
		--rene-far-left: 5px;
	}

	h1 {
		font-size: 3.5rem;
		text-align: center;
		margin: 0 10px;
    color: var(--primary-color);
	}

	.heading > p {
		text-align: center;
		font-size: 2rem;
		margin-top: 0;
		color: var(--primary-color-light);;
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

	@media (max-width: 478px) {
		.heading > img {
			top: 66px;
		}
	}

  p,
	ol,
  ul {
		font-size: 1.3rem;
	}

  p {
    margin: 15px 25px;
    line-height: 1.7rem;
  }

	code {
		color: blueviolet;
    font-family: monospace;
	}

	em {
		font-weight: 900;
    font-size: 1.4rem;
		color: rgb(0, 124, 128);
	}

	li {
		margin-top: 1rem;
	}

	article {
		margin-top: 20vh;
	}

	.first-article {
		margin: 10vh 5% 0 0;
    display: flex;
    align-items: center;
	}

  .left {
    flex-grow: 2;
    padding-right: 10%;
  }

  .right {
    width: 300px;
    flex-shrink: 0;
    align-self: stretch;

  }


  .first-article img {
    width: 100%;
    height: 100%;
    object-position: 80% center;
    object-fit: cover;
  }


  @media (max-width:900px) {
    .left {
      padding-right: 5%;
    }
  }

  @media (max-width:850px) {
    .left {
      padding-right: 0%;
    }
  }

  @media (max-width:810px) {
    .first-article {
      flex-direction: column;
      margin-right: 0;
    }

    .right {
      height: 350px;
      width: 100%;
    }
  }


	.small-ol > li {
		margin-top: 0.5rem;
	}

	.info {
		background-color: rgb(210, 243, 250);
		font-size: 1.2rem;
    padding: 10px 20px;
	}

	.long-code {
		background-color: rgb(250, 247, 210);
		padding: 10px 30px;
	}

	.long-code > p {
		margin: 0;
		font-size: 1.1rem;
	}

	.mb-40 {
		margin-bottom: 40px;
	}
  .pl-20 {
		padding-left: 20px;
	}

  h2 span {
    color: var(--primary-color-light);
    font-size: 1.2rem;
  }

  h2 {
    color: var(--primary-color);
    font-size: 2.5rem;
    margin: 0 25px;
  }
</style>