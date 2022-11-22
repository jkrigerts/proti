<div class="outer">
	<div class="inner">
		<a class="sm" href="/if.pdf">if prezentācija</a>
		<div class="lg">
			<h2>if prezentācija</h2>
			<iframe title="Sarošanās jeb if" src="/if.pdf" height="400" width="700" />
		</div>
	</div>
</div>
<div class="outer">
	<div class="inner">
		<a class="sm" href="/KSIM2022_fin_uzd.pdf">KSIM uzdevumi</a>
		<div class="lg">
			<h2>KSIM uzdevumi</h2>
			<iframe title="Sarošanās jeb if" src="/KSIM2022_fin_uzd.pdf" height="400" width="700" />
		</div>
	</div>
</div>

<style>
	.outer {
		width: 100vw;
		height: 80vh;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.inner {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	a {
		width: 200px;
		text-decoration: none;
		color: white;
		padding: 15px 20px;
		border-radius: 3px;
		font-weight: 600;
		background-color: blueviolet;
		margin-bottom: 30px;
		font-family: Verdana, Geneva, Tahoma, sans-serif;
		text-align: center;
		transition: all 0.4s;
	}
	a:hover {
		background-color: blue;
	}

	h2 {
		color: purple;
		font-family: Verdana, Geneva, Tahoma, sans-serif;
	}

	.lg {
		display: none;
	}

	@media (min-width: 740px) {
		.sm {
			display: none;
		}

		.lg {
			display: block;
		}
	}
</style>
