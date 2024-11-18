<script>
	import LazyComponent from '$lib/LazyComponent.svelte';

	let targetDoneEl = $state(null);
	$inspect(targetDoneEl);
	let done = $derived(!!targetDoneEl);

	let inputValue = $state('');
</script>

<h1>Welcome to your library project</h1>
<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

<p>Not yet supported for bindable props, use change handler instead</p>

<a href="https://github.com/binsarjr/svelte-lazy-component/blob/main/src/lib/LazyComponent.svelte"
	>Code Here</a
>

{#snippet justForWaiting()}
	{#each { length: 20 } as _}
		{#if done}
			<div>Done Loaded All Lazy Component</div>
		{:else}
			<div>scroll down (see your network traffic)</div>
		{/if}
	{/each}
{/snippet}

{@render justForWaiting()}

{#each { length: 5 } as _, i}
	{@const avatar = `https://picsum.photos/200/200?id=${i}`}
	{@const name = `${Math.random() * 1000}`}
	{@const content = `${Math.random() * 1000}`}
	<LazyComponent
		component={() => import('$components/GalleryPhoto.svelte')}
		{avatar}
		{name}
		{content}
	/>
{/each}

{@render justForWaiting()}
<LazyComponent
	component={() => import('$components/Input.svelte')}
	defaultValue="Hello From Lazy Loaded"
/>

<div>
	<div>
		<p>Hello Outside: {inputValue}</p>
	</div>
	<LazyComponent
		component={() => import('$components/Input.svelte')}
		defaultValue="Hello From Lazy Loaded"
		onInput={(event) => {
			inputValue = event.target.value;
		}}
	/>
</div>
{@render justForWaiting()}

<LazyComponent component={() => import('$components/Hello.svelte')} ok="yuuuuhuu">
	<div bind:this={targetDoneEl}>Loaded</div>
	heheh boy
</LazyComponent>
