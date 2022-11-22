<div class="container">
	<h1 class="greeting">Sveicināti! <em class="proti">proti.lv</em>!</h1>
</div>

<footer><a href="/sp">Sporta programmēšana</a></footer>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,400;1,300&display=swap');

	.container {
		font-family: 'Josefin Sans', sans-serif;
		width: 100vw;
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 0;
	}

	.greeting {
		margin: 20px;
		text-align: center;
	}

	.proti {
		font-style: italic;
		font-size: 1.3em;
		color: rgb(132, 23, 233);
	}

	footer {
		display: block;
		width: 100%;
		position: fixed;
		bottom: 0;
		left: 0;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	footer > a {
		display: block;
		text-decoration: none;
		margin-bottom: 1rem;
		color: rgba(132, 23, 233, 0.3);
		transition: all 0.4s;
	}

	footer > a:hover {
		color: rgba(132, 23, 233, 0.6);
	}
</style>
