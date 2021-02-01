<script>
	const ratio = 166.386;

	let euros = 0;
	let pesetas = 0;

	function onChangeEuros() {
	  pesetas = (euros * ratio).toFixed(2);
	}

	function onChangePesetas() {
	  euros = (pesetas / ratio).toFixed(2);
	}
</script>

<style>
	.app {
	  margin: 1rem;
	  display: flex;
	  align-items: center;
	  justify-content: center;
	  height: 90vh;
	  font: 40px sans-serif;
	}

	.container {
	  display: grid;
	  grid-template-columns: 2fr 3fr;
	  align-items: center;
	  grid-gap: 1rem;
	  width: 100%;
	  max-width: 800px;
	}

	.currency-title {
	  text-align: right;
	}

	.currency-input {
	  font: inherit;
	  padding: 0.5rem;
	  width: 100%;
	  box-sizing: border-box;
	}

	@media (max-width: 600px) {
	  .container {
	    grid-template-columns: 1fr;
	  }

	  .currency-title, .currency-input {
	    text-align: center;
	  }
	}

	.repo {
		display: block;
		color: lightcoral;
		font: 12px monospace;
		text-align: center;
		text-decoration: none;
	}
</style>

<div class=app>
	<div class=container>
		<span class=currency-title>Euros</span>
		<input
			class=currency-input
			type=number
			bind:value={euros}
			on:input={onChangeEuros}
		>

		<span class=currency-title>Pesetas</span>
		<input
			class=currency-input
			type=number
			bind:value={pesetas}
			on:input={onChangePesetas}
		>
	</div> <!-- .container -->
</div> <!-- .app -->

<a class=repo href=https://github.com/marionauta/euros-a-pesetas target=_blank>
	código de la app
</a>
