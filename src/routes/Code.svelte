<script>
  import { onMount } from 'svelte';
	import Room from './Room.svelte';

  export let rows = 4;
  export let columns = 4;
  export let reneInit = [0, 0, 0];
  export let targetInit = [-1, -1];
  export let boxInit = [-1, -1];
  export let obstacles = [];
  export let no = 0;
  export let aim = "target";
  export let handleScore;

  export let customCommands = [];
  export let handleCustomCommands;

  let code = "";
  let success = false;
  let loading = false;
  let reneX = reneInit[0];
  let reneY = reneInit[1];
  let reneD = reneInit[2];
  let target = [...targetInit];
  let box = [...boxInit];
  let error = false;

  let hasBox = false;
  let boxOnTarget = false;
  let time = 1000;

  const directionMap = [
    [1, 0],
    [0, 1],
    [-1, 0],
    [0, -1]
  ];

  let commands = [
    "iet", "ņemt", "likt", "paLabi", "ātrums"
  ]

  $: commands = [...commands, ...Object.keys(customCommands)];

  onMount(() => {
    code = localStorage.getItem(`room-${no}`) || "";
    success = localStorage.getItem(`room-${no}-success`) || false;
    if (localStorage.getItem(`room-${no}-success`)) handleScore();
    lineNumbersHanler();
  })

  function delay() {
    return new Promise(resolve => setTimeout(resolve, time));
  }

  const toLocalStorage = () => {
    localStorage.setItem(`room-${no}`, code)
  }

  const matchCommandAndComplete = async (cleansedLine) => {
    switch (cleansedLine) {
        case ("iet();"):
          await move();
          break;
        case ("ņemt();"):
          await pickUp();
          break;
        case ("paLabi();"):
          await turnRight();
          break;
        case ("likt();"):
          await putDown();
          break;
        default:
          alert("Komanda netika atpazīta!");
      }
  }

  const runCode = async () => {
    loading = true;
    time = 1000;
    reneX = reneInit[0];
    reneY = reneInit[1];
    reneD = reneInit[2];
    box = [...boxInit];
    hasBox = false;
    toLocalStorage();
    const splitedLines = code.split(/\r?\n/);

    let newCommandName = "";
    let newCommandUnderWay = false;
    let newCommandSequence = [];
    for (const line of splitedLines) {
      const cleansedLine = line.trim();
      if (cleansedLine == "") continue;
      if (error) {
        error = false;
        loading = false;
        return;
      }
      if (newCommandUnderWay) {
        if (cleansedLine.startsWith("}")) {
          handleCustomCommands(newCommandName, newCommandSequence);
          for (const com of customCommands[newCommandName]) {
            await matchCommandAndComplete(com);
          }
          newCommandUnderWay = false;
          continue;
        }
        if (commands.includes(cleansedLine.slice(0, -3))) {
          newCommandSequence = [...newCommandSequence, cleansedLine];
        } else if (cleansedLine.includes("ātrums") || cleansedLine.includes("reizes")) {
          alert("Prasmē nevar izmantot ātrumu un reizes!");
          loading = false;
          return;
        } else {
          alert(`Nederīga komanda jaunajā prasmē: ${cleansedLine}`);
          loading = false;
          return;
        }
        continue;
      }

      if (cleansedLine.startsWith("prast")) {
        if (!cleansedLine.endsWith("{")) {
          alert("Vai jaunās komandas 1. rindiņa beidzas ar atverošo figūriekavu?");
          loading = false;
          return;
        }
        const newCommandArray = cleansedLine.match(/prast\s+[a-zA-ZāčēģīķļņšūžĀČĒĢĪĶĻŅŠŪŽ]+\(\)/);
        if (!newCommandArray) {
          alert("Jaunajai komandai ir nederīgs nosaukums!");
          loading = false;
          return;
        }
        newCommandName = newCommandArray[0].slice(6, -2).trim();
        if (commands.includes(newCommandName) && !Object.keys(customCommands).includes(newCommandName)) {
          alert("Jaunās komandas nosaukums nedrīkst sakrist ar esošas komandas nosaukumu!");
          loading = false;
          return;
        }
        newCommandUnderWay = true;
        continue;
      }

      if (!cleansedLine.endsWith(";")) {
        alert("Vai katra rindiņa beidzas ar semikolu?");
        loading = false;
        return;
      }
      
      let count = 0;
      for (const command of commands) {
        const reg = new RegExp(`${command}();`, "g");
        count += (cleansedLine.match(reg) || []).length;
      }
      if ((cleansedLine.match(/;/g) || []).length > 1 || count > 1) {
        alert("Katrā rindiņā ir atļauta tikai viena komanda!");
        loading = false;
        return;
      }
      if (cleansedLine.startsWith("ātrums")) {
        const speed = Number(cleansedLine.match(/\(.*\)/)[0].slice(1, -1).replace(",", "."));
        if(!speed) {
          alert ("Apaļajās iekavās jānorāda ātruma lielums - skaitlis bez atstarpēm!");
          loading = false;
          return;
        }
        setSpeed(speed);
        continue;
      }

      if (cleansedLine.startsWith("reizes")) {
        const repeatHasNumbers = cleansedLine.match(/\s[0-9]+\s/);
        if (!repeatHasNumbers && cleansedLine.match(/[0-9]+/)) {
          alert ("Arī tukšuma rakstzīmes ir būtiskas!");
          loading = false;
          return;
        }
        if (!repeatHasNumbers) {
          alert ("Nav noteikts, cik reizes atkārtot!");
          loading = false;
          return;
        }
        if (cleansedLine.includes("ātrums")) {
          alert ("Ātrumu nav iespējams atkārtot!");
          loading = false;
          return;
        }
        const repeatTimes = Number(repeatHasNumbers[0].trim());

        const repeatHasCommand = cleansedLine.match(/[a-zA-ZāčēģīķļņšūžĀČĒĢĪĶĻŅŠŪŽ]+\(\);/);
        if (!repeatHasCommand) {
          alert("Atkārtojumā ir jādod komanda!");
          loading = false;
          return;
        }
        if (!commands.includes(repeatHasCommand[0].slice(0, -3))) {
          alert("Atkārtojumā dotā komanda nav atrasta!");
          loading = false;
          return;
        }
        const repeatCommand = repeatHasCommand[0];

        await repeatLoop(repeatTimes, repeatCommand);
        continue;
      }

      if (!cleansedLine.endsWith("();")) {
        alert("Vai izsauci funkciju ar apaļajām iekavām?");
        loading = false;
        return;
      }

      if (cleansedLine.slice(0, -3) in customCommands) {
        for (const com of customCommands[cleansedLine.slice(0, -3)]) {
          await matchCommandAndComplete(com);
        }
        continue;
      }
      await matchCommandAndComplete(cleansedLine);
    }

    if (newCommandUnderWay) {
      alert("Jaunā komanda nekad netika pabeigta ar aizverošo figūriekavu!");
      loading = false;
      return;
    }
    checkSuccess();
    loading = false;
  }

  const checkSuccess = () => {
    if (success) return;
    if (aim == "box" && hasBox) {
      handleScore();
      success = true;
      localStorage.setItem(`room-${no}-success`, true);
    }

    if (aim == "target" && boxOnTarget) {
      handleScore();
      success = true;
      localStorage.setItem(`room-${no}-success`, true);
    }

    if (aim == "turnLeft") {
      let rightCounter = 0;
      for (const com of customCommands["paKreisi"] || []) {
        if (com == "paLabi();") {
          rightCounter++;
        }
      }
      if (rightCounter != 0 && rightCounter % 3 == 0) {
        handleScore();
        success = true;
        localStorage.setItem(`room-${no}-success`, true);
      }
    }
  }

  const move = async () => {
    await delay();
    const tmpX = reneX + directionMap[reneD][0]
    const tmpY = reneY + directionMap[reneD][1];
    if (tmpX < 0 || tmpX == columns || tmpY < 0 || tmpY == rows) {
      alert("Rene ieskrēja sienā!");
      reneX = reneInit[0];
      reneY = reneInit[1];
      reneD = reneInit[2];
      box = [...boxInit];
      error = true;
      return;
    }
    for (const obstacle of obstacles) {
      if (tmpX == obstacle[0] && tmpY == obstacle[1]) {
        alert("Rene ieskrēja šķērslī!");
        reneX = reneInit[0];
        reneY = reneInit[1];
        reneD = reneInit[2];
        box = [...boxInit];
        error = true;
        return;
      }
    }
    reneX = tmpX;
    reneY = tmpY;
  }

  const pickUp = async () => {
    await delay();

    if (reneX == box[0] && reneY == box[1]) {
      hasBox = true;
      box = [-1, -1];
    }
  }

  const turnRight = async () => {
    await delay();
    reneD = reneD == 3 ? 0 : reneD+1;
  }

  const putDown = async () => {
    await delay();
    if (hasBox) {
      box = [reneX, reneY];
      hasBox = false;
    }

    if (box[0] >= 0 && box[0] == target[0] && box[1] >=0 && box[1] == target[1]) {
      boxOnTarget = true;
    }
  }

  const setSpeed = (x) => {
    time = 1000/x;
  }

  const repeatLoop = async (n, command) => {
    for (let i = 0; i < n; i++) {
      await matchCommandAndComplete(command);
    }
  }

  let numberOfLines = 1;
  let textareaHeight = 32;
  const lineNumbersHanler = () => {
    numberOfLines = code.split('\n').length;
    textareaHeight = 32 + (32 * numberOfLines);
  } 
</script>


<div class="container">
  <div class="code-wrapper" style="--textarea-height:{textareaHeight}px;">
    <div class="code">
      <div class="line-numbers">
          {#each Array(numberOfLines-1) as i}
            <span></span>
          {/each}
          <span></span>
      </div>
      <textarea bind:value={code} on:keyup={lineNumbersHanler} placeholder="Šiet jāraksta komandas"/>
    </div>
    <button on:click={runCode} style={`--success:${success ? "green" : "white"}; color:${success ? "white" : "black"}`} disabled={loading}>Izpild{loading ? "a..." : success ? "īts" : "īt"}</button>
    {#if success}
      <img src="check.webp" alt="Check" class="success"/>
     {/if}
  </div>
  <Room rows={rows} columns={columns} start={[reneInit[0], reneInit[1]]} reneX={reneX} reneY={reneY} reneD={reneD} target={target} box={box} obstacles={obstacles}/>

</div>

<style>
  .container {
    display: flex;
  }

  button {
    position: absolute;
    bottom: max(calc(var(--screen-height) - var(--textarea-height)), 20px);
    left:8%;
    cursor: pointer;
    padding: 10px 20px;
    width: 84%;
    box-sizing: border-box;
    background-color: var(--success);
    border: none;
    transition: all 0.3s;
  }

  .code-wrapper {
    --screen-height: 50vh;
  }

  button:disabled {
    cursor: not-allowed;
  }

  .success {
    position: absolute;
    bottom: max(calc(var(--screen-height) - var(--textarea-height)), 20px);
    left:8%;
    width: 50px;
    transition: all 0.3s;
  }

  button::before {
    position: absolute;
    top:0;
    left: 0;
    content: "";
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    display: block;
    border: 2px solid var(--success);
    transition: all 0.3s;
  }

  button:hover::before {
    transform: scaleX(1.05) scaleY(1.5);
  }

  .code-wrapper {
    position: relative;
    width: 34%;
    background: #282a3a;
    padding: 30px 0px;
  }

  .code {
    display: flex;
    gap: 13px;
    font-family: monospace;
    line-height: 32px;
    border-radius: 2px;
    height: 60vh;
    box-sizing: border-box;
    overflow-y: scroll;
  }

  textarea {
    line-height: inherit;
    height: var(--textarea-height);
    min-height: 40vh;
    padding: 0;
    border: 0;
    background: #282a3a;
    color: #FFF;
    outline: none;
    resize: none;
    font-size: 18px;
    width: calc(100% - 25px);
    overflow: hidden;
  }

  .line-numbers {
    width: 20px;
    font-size: 18px;
    text-align: right;
    line-height: 32px;
  }

  span {
    counter-increment: linenumber;
  }

  span::before {
    content: counter(linenumber);
    display: block;
    color: #506882;
    transform: scale(0.8) translateX(5px) translateY(3px);
  }

  @media (max-width: 820px) {
    .container {
      flex-direction: column;
    }

    .code-wrapper {
      width: 100%;
      --screen-height: 15vh;
    }

    .code {
      height: 24vh;
      margin-bottom: 4vh;
    }

    textarea {
      min-height: 15vh;
    }
  }
</style>