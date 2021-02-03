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
		flex-grow: 1;
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
		width: 100%;
		padding: .5rem 1rem;
		box-sizing: border-box;
		background: var(--color-background);
		border: 2px solid var(--color-foreground);
		border-radius: .25rem;
		color: var(--color-foreground);
		outline: none;
	}

	.currency-input:focus {
		border-color: var(--color-accent);
	}

	@media (max-width: 600px) {
		.container {
			grid-template-columns: 1fr;
		}

		.currency-title, .currency-input {
			text-align: center;
		}
	}

	.footer {
		margin: 1rem;
		font: 14px monospace;
		text-align: center;
	}

	.footer a {
		color: var(--color-accent);
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
			inputmode=decimal
			bind:value={euros}
			on:input={onChangeEuros}
		>

		<label for=peseta-input class=currency-title>Pesetas</label>
		<input
			id=peseta-input
			class=currency-input
			placeholder=0
			inputmode=decimal
			bind:value={pesetas}
			on:input={onChangePesetas}
		>
	</div> <!-- .container -->
</div> <!-- .app -->

<div class=footer>
	<div class=ratio>1 euro = 166,386 pesetas</div>
	<a href={creator.repo} target=_blank rel=noopener>código de la app</a> ·
	<a href={creator.link} target=_blank rel=noopener>{creator.name}</a>
</div>
