<script>
	let snowing = true;
</script>

<div class="toggle">
	<div class="letitsnow">Lai snieg!</div>
	<div class="toggle-inner">
		<input type="checkbox" id="switch" bind:checked={snowing} />
		<label for="switch" />
	</div>
</div>

{#if snowing}
	<div class="snowflakes" aria-hidden="true">
		<div class="snowflake">❅</div>
		<div class="snowflake">❆</div>
		<div class="snowflake">❅</div>
		<div class="snowflake">❆</div>
		<div class="snowflake">❅</div>
		<div class="snowflake">❆</div>
		<div class="snowflake">❅</div>
		<div class="snowflake">❆</div>
		<div class="snowflake">❅</div>
		<div class="snowflake">❆</div>
		<div class="snowflake">❅</div>
		<div class="snowflake">❆</div>
	</div>
{/if}

<style>
	.letitsnow {
		margin-right: 20px;
	}
	.toggle {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.toggle-inner {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	input[type='checkbox'] {
		height: 0;
		width: 0;
		visibility: hidden;
		margin: 0;
	}

	label {
		cursor: pointer;
		width: 70px;
		height: 40px;
		background: #031050;
		display: block;
		border-radius: 100px;
		position: relative;
		white-space: nowrap;
	}

	label:after {
		content: 'Nē';
		line-height: 1.8;
		text-align: center;
		color: #031050;
		font-size: 16px;
		position: absolute;
		top: 5px;
		right: 5px;
		width: 30px;
		height: 30px;
		background: whitesmoke;
		border-radius: 90px;
		transition: 0.3s;
	}

	input:checked + label {
		background: #ce6e07;
	}

	input:checked + label:after {
		content: 'Jā';

		color: #ce6e07;
		right: 5px;
		transform: translateX(-100%);
	}

	/* label:active:after {
		width: 130px;
	} */

	/* customizable snowflake styling */
	.snowflake {
		color: #fff;
		font-size: 1em;
		font-family: Arial, sans-serif;
		text-shadow: 0 0 5px #031050bf;
	}

	@-webkit-keyframes snowflakes-fall {
		0% {
			top: -30px;
		}
		100% {
			top: 100vh;
		}
	}
	@-webkit-keyframes snowflakes-shake {
		0%,
		100% {
			-webkit-transform: translateX(0);
			transform: translateX(0);
		}
		50% {
			-webkit-transform: translateX(80px);
			transform: translateX(80px);
		}
	}
	@keyframes snowflakes-fall {
		0% {
			top: -30px;
		}
		100% {
			top: 100vh;
		}
	}
	@keyframes snowflakes-shake {
		0%,
		100% {
			transform: translateX(0);
		}
		50% {
			transform: translateX(80px);
		}
	}
	.snowflake {
		position: fixed;
		top: -30px;
		z-index: 9999;
		-webkit-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
		cursor: default;
		-webkit-animation-name: snowflakes-fall, snowflakes-shake;
		-webkit-animation-duration: 10s, 3s;
		-webkit-animation-timing-function: linear, ease-in-out;
		-webkit-animation-iteration-count: infinite, infinite;
		-webkit-animation-play-state: running, running;
		animation-name: snowflakes-fall, snowflakes-shake;
		animation-duration: 10s, 3s;
		animation-timing-function: linear, ease-in-out;
		animation-iteration-count: infinite, infinite;
		animation-play-state: running, running;
	}
	.snowflake:nth-of-type(0) {
		left: 1%;
		-webkit-animation-delay: 0s, 0s;
		animation-delay: 0s, 0s;
	}
	.snowflake:nth-of-type(1) {
		left: 10%;
		-webkit-animation-delay: 1s, 1s;
		animation-delay: 1s, 1s;
	}
	.snowflake:nth-of-type(2) {
		left: 20%;
		-webkit-animation-delay: 6s, 0.5s;
		animation-delay: 6s, 0.5s;
	}
	.snowflake:nth-of-type(3) {
		left: 30%;
		-webkit-animation-delay: 4s, 2s;
		animation-delay: 4s, 2s;
	}
	.snowflake:nth-of-type(4) {
		left: 40%;
		-webkit-animation-delay: 2s, 2s;
		animation-delay: 2s, 2s;
	}
	.snowflake:nth-of-type(5) {
		left: 50%;
		-webkit-animation-delay: 8s, 3s;
		animation-delay: 8s, 3s;
	}
	.snowflake:nth-of-type(6) {
		left: 60%;
		-webkit-animation-delay: 6s, 2s;
		animation-delay: 6s, 2s;
	}
	.snowflake:nth-of-type(7) {
		left: 70%;
		-webkit-animation-delay: 2.5s, 1s;
		animation-delay: 2.5s, 1s;
	}
	.snowflake:nth-of-type(8) {
		left: 80%;
		-webkit-animation-delay: 1s, 0s;
		animation-delay: 1s, 0s;
	}
	.snowflake:nth-of-type(9) {
		left: 90%;
		-webkit-animation-delay: 3s, 1.5s;
		animation-delay: 3s, 1.5s;
	}
	.snowflake:nth-of-type(10) {
		left: 25%;
		-webkit-animation-delay: 2s, 0s;
		animation-delay: 2s, 0s;
	}
	.snowflake:nth-of-type(11) {
		left: 65%;
		-webkit-animation-delay: 4s, 2.5s;
		animation-delay: 4s, 2.5s;
	}
</style>
