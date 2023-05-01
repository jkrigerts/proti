<script>
  export let rows = 4;
  export let columns = 4;
  export let reneX = 0;
  export let reneY = 0;
  export let reneD = 0;
  export let box = [2, 2];
  export let target = [1, 1];
  export let start = [0, 0];
  export let obstacles = [];
</script>

<div class="room" style="--rows: {rows}; --columns: {columns}; --direction: {reneD == 2 ? 0 : reneD}; --flip: {reneD == 2 ? -1 : 1}">
  {#each { length: rows} as _, i }
    {#each { length: columns} as _, j }
      <div class="step" id={`${i}-${j}`}>
        {#each obstacles as obstacle}
          {#if j == obstacle[0] && i == obstacle[1]}
            <div class="obstacle">
            </div>
          {/if}
        {/each}
        {#if j == start[0] && i == start[1]}
          <div class="start">
          </div>
        {/if}
        {#if j == reneX && i == reneY}
          <div class="img-wrapper rene">
            <img src="rene.png" alt="Rene"/>
          </div>
        {/if}
        {#if j == target[0] && i == target[1]}
          <div class="img-wrapper">
            <img src="target.png" alt="Target" />
          </div>
        {/if}
        {#if j == box[0] && i == box[1]}
          <div class="img-wrapper">
            <img src="box.png" alt="Box" />
          </div>
        {/if}
        {#if j == box[0] && i == box[1] && box[0] == target[0] && box[1] == target[1]}
          <div class="img-wrapper checkmark" >
            <img src="check.webp" alt="Check"/>
          </div>
        {/if}
      </div>
    {/each}
  {/each}
</div>

<style>
  .room {
    width: 66%;
    margin: 0 auto;
    height: 74vh;
    display: grid;
    grid-template-columns: repeat(var(--columns), minmax(0, 1fr));
    grid-template-rows: repeat(var(--rows), minmax(0, 1fr));
    background-color: #330088;
    border: 1px solid #330088;
    border-right: none;
    border-left: none;
    gap: 1px;
  }

  @media (max-width: 820px) {
    .room {
      width: 100%;
      height: 60vh;
    }
  }

  @media (max-width: 520px) {
    .room {
      height: 45vh;
    }
  }

  .step {
    background-color: whitesmoke;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  img {
    
    object-fit: contain;
    height: 100%;
    width: 100%;
  }

  .img-wrapper {
    position: absolute;
    top:0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 10;
  }

  .obstacle {
    background-color: var(--primary-color-light);
    width: 100%;
    height: 100%;
  }

  .start {
    background-color: rgb(225, 245, 225);
    width: 100%;
    height: 100%;
  }

  .rene {
    transform: rotate(calc(var(--direction) * 90deg)) scaleX(var(--flip));
    z-index: 11;
  }

  .checkmark {
    z-index: 12;
    animation: 1s checkZoom 0s, 1.4s checkPulse 1s infinite;
    margin: 0 auto;
    transform: scale(1.1);
  }

  @keyframes checkZoom {
    0% {
      transform: scale(0);
    }
    100% {
      transform: scale(1.1);
    }
  }

  @keyframes checkPulse {
    0% {
      transform: scale(1.1);
    }
    50% {
      transform: scale(1.2);
    }
    100% {
      transform: scale(1.1);
    }
  }
</style>