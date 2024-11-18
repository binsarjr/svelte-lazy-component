<script>
	import LazyComponent from '$lib/LazyComponent.svelte';

	let targetDoneEl = $state(null);
	let done = $derived(!!targetDoneEl);
</script>

<h1>Welcome to your library project</h1>
<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>
<a href="">Code Here</a>

{#each { length: 10 } as _}
	{#if done}
		<div>Loaded</div>
	{:else}
		<div>scroll down (see your network traffic)</div>
	{/if}
{/each}

<LazyComponent component={() => import('$components/Hello.svelte')} ok="sip">
	<div bind:this={targetDoneEl}>Loaded</div>
	heheh boy
</LazyComponent>
