<script>
	let { defaultValue, onInput, ...Props } = $props();

	let value = $state(defaultValue);
</script>

<div {...Props}>
	<label>
		<p>Hello Inside: {value}</p>
		<input type="text" bind:value oninput={onInput} />
	</label>
</div>
