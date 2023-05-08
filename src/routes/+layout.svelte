<main>
  <slot />
</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,400;1,300&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Source+Code+Pro&display=swap');

	* {
		box-sizing: border-box;
	}
  :global(body) {
    --primary-color: #282560;
    --primary-color-light: #474667;
		background: var(--primary-color);
    margin: 0;
  }

  :global(html) {
    scroll-behavior: smooth;
  }

  main {
    max-width: 1180px;
    margin: 0 auto;
    background-color: whitesmoke;
    font-family: 'Josefin Sans', sans-serif;
  }

  @media (max-width: 1220px) {
    main {
      margin: 0 20px;
    } 
  }

  @media (max-width: 1000px) {
    main {
      margin: 0 10px;
    } 
  }

  @media (max-width: 340px) {
    main {
      margin: 0;
    } 
  }
</style>