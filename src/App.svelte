<script>
	import marked from 'marked';
	
	let markdown = '';
	let showInputPanel = true;
</script>

<main>
	<div class="button-row">
		<button on:click={() => markdown = ''}>
			Clear
		</button>
		<button on:click={() => showInputPanel = !showInputPanel}>
			{showInputPanel ? 'Hide' : 'Show'} input panel
		</button>
	</div>
	<div class="io">
		{#if showInputPanel}
					<textarea id="input" class="io-container" bind:value={markdown}></textarea>
		{/if}
			<div id="output" class="io-container padding">{@html marked(markdown)}</div>
	</div>
</main>

<style>
	main {
		height: 100%;
		width: 100%;
		display: flex;
		flex-flow: column nowrap;
		padding: 8px;
	}
	.button-row {
		display: flex;
		flex-flow: row nowrap;
	}
	.button-row > * {
		margin: 4px;
	}
	.button-row > *:first-child {
		margin-left: 2px;
		margin-right: 2px;
	}
	.io {
		width: 100%;
		display: flex;
		flex-flow: row nowrap;
		flex-grow: 1;
	}
	.io-container {
		border: 1px solid #999;
		border-radius: 2px;
		width: 100%;
		min-width: 50%;
		height: 100%;
		margin: 2px;
	}
	textarea {
		resize: none;
	}
</style>