<script>
  import { fade, fly } from 'svelte/transition';
  import { Confetti } from "svelte-confetti";


  export let handleClose;
</script>

<div class="backdrop" transition:fade>
  <div class="modal" transition:fly="{{ y: 200, duration: 2000 }}">
    <div class="close">
      <img src="close.svg" alt="X" on:click={handleClose}/>
    </div>
    <h1>Apsveicu!</h1>
    <h2>🥳</h2>
    <p>Tu veiksmīgi esi ticis galā ar ievadu programmēšanā! 🙂</p>
    <p>Nākošais līmenis - iestāties <a target="_blank" href="https://www.vtdt.lv/"><em>Vidzemes Tehnoloģiju un dizaina tehnikumā</em></a>!</p>
  </div>
</div>

<div class="confetti" transition:fade>
<Confetti x={[-5, 5]} y={[0, 0.1]} delay={[500, 2000]} infinite duration=5000 amount=200 size=13 fallDistance="100vh" />
</div>

<style>
  .backdrop {
    position: fixed;
    top:0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(245, 245, 245, 0.46);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 997;
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px);
    overflow: hidden;
  }

  .modal {
    width: 400px;
    max-width: 95vw;
    background-color: whitesmoke;
    padding: 30px 20px;
    box-sizing: border-box;
    position: relative;
    transform: translateY(-20px);
    border: 3px solid var(--primary-color);
  }

  h1, h2 {
    font-size: 3rem;
    text-align: center;
    margin: 0;
  }

  p {
    font-size: 1.3rem;
  }

  em {
    color: var(--primary-color);
    font-size: 1.4rem;
    font-weight: 900;
  }

  .close {
    position: absolute;
    top: 0px;
    right: 0px;
    width: 35px;
    height: 35px;
    cursor: pointer;
  }

  .close > img {
    width: 100%;
    height: 100%;
  }

  .confetti {
    position: fixed;
    top: -50px;
    left: 0;
    height: 100vh;
    width: 100vw;
    display: flex;
    justify-content: center;
    overflow: hidden;
    pointer-events: none;
    z-index: 998;
  }
</style>