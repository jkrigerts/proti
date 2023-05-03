<script>
  import { fade, fly } from 'svelte/transition';

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
    z-index: 998;
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
</style>