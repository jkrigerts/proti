<script>
  export let globalScore;
  export let totalScore = 9;
  export let reset;
</script>

<div>
  <p>Rezultāts: <span>{globalScore} / {totalScore}</span></p>
  <button on:click={reset()}><img src="trash-solid.svg" alt="Dzēst" /> </button>
</div>

<style>
  div {
    position: fixed;
    top: 20px;
    right: 20px;
    width: 200px;
    height: 50px;
    background-color: whitesmoke;
    display: flex;
    justify-content: space-around;
    align-items: center;
    border: 3px solid var(--primary-color);
    z-index: 999;

  }

  span {
    font-size: 1.4rem;
  }

  button {
    background-color: transparent;
    border: none;
    cursor: pointer;
    transition: all 0.3s;
  }

  button:hover {
    transform: rotate(15deg) scale(1.1);
  }

  img {
    width: 16px;
  }
</style>