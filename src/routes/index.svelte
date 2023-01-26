<div class="container">
	<h1 class="greeting">Sveicināti <em class="proti">proti.lv</em>!</h1>
	<a class="btn" href="/ai">Atvērto durvju diena</a>
	<a href="/btn.txt" download>Pogas efekta atrisinājums. Tev tips uz .html jāmaina</a>
	<a class="btn" href="https://skolo.lv/course/view.php?id=742234">JPS skolo.lv</a>
</div>

<footer>
	<a href="/christmas">Draugiem Group konkurss</a><a href="/sp">Sporta programmēšana</a>
</footer>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,400;1,300&display=swap');

	.container {
		font-family: 'Josefin Sans', sans-serif;
		width: 100vw;
		height: 90vh;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		margin: 0;
		gap: 30px;
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
		width: 100%;
		position: fixed;
		bottom: 0;
		left: 0;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	footer > a {
		text-decoration: none;
		margin-bottom: 1rem;
		color: rgba(132, 23, 233, 0.3);
		transition: all 0.4s;
	}

	footer > a:first-child {
		margin-right: 20px;
	}

	footer > a:hover {
		color: rgba(132, 23, 233, 0.6);
	}

	.btn {
		padding: 15px 20px;
		font-size: 1.2rem;
		background-color: rgb(132, 23, 233);
		color: white;
		text-decoration: none;
		position: relative;
	}

	.btn:hover {
		background-color: rgb(96, 17, 169);
		cursor: pointer;
	}

	.btn::before {
		content: '';
		border: 2px solid rgb(132, 23, 233);
		padding: inherit;
		position: absolute;
		inset: 0;
		opacity: 1;
		transition: all 0.5s;
	}

	.btn:hover::before {
		transform: scaleX(1.2) scaleY(1.5);
		opacity: 0;
	}
</style>
