<script>
	const creator = {
		name: 'Mario Nachbaur',
		link: 'https://mario.nachbaur.dev',
		repo: 'https://github.com/marionauta/euros-a-pesetas',
	};

	const ratio = 166.386;
	const formatter = Intl.NumberFormat('default', {
		minimumFractionDigits: 2,
		maximumFractionDigits: 2,
	});

	let euros = '';
	let pesetas = '';

	function cleanInput(input) {
		return parseFloat(input.replaceAll('.', '').replaceAll(',', '.'), 10);
	}

	function onChangeEuros() {
		const value = euros.length ? cleanInput(euros) : 0;
		pesetas = value ? formatter.format(value * ratio) : '';
	}

	function onChangePesetas() {
		const value = pesetas.length ? cleanInput(pesetas) : 0;
		euros = value ? formatter.format(value / ratio) : '';
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

	.attribution {
		display: block;
		font: 12px monospace;
		text-align: center;
		text-decoration: none;
	}

	.attribution a {
		color: #f08080;
		text-decoration: none;
	}
</style>

<div class=app>
	<div class=container>
		<label for=euro-input class=currency-title>Euros</label>
		<input
			id=euro-input
			class=currency-input
			placeholder=0
			bind:value={euros}
			on:input={onChangeEuros}
		>

		<label for=peseta-input class=currency-title>Pesetas</label>
		<input
			id=peseta-input
			class=currency-input
			placeholder=0
			bind:value={pesetas}
			on:input={onChangePesetas}
		>
	</div> <!-- .container -->
</div> <!-- .app -->

<div class=attribution>
	<div class=ratio>1 euro = {ratio} pesetas</div>
	<a href={creator.repo} target=_blank rel=noopener>código de la app</a> #
	<a href={creator.link} target=_blank rel=noopener>creado por {creator.name}</a>
</div>
