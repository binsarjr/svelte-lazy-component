<script>
	import { inview } from 'svelte-inview';

	let { component, loaderFn, fallbackFn, ...comopnentProps } = $props();

	let isInView = $state(false);
</script>

<div
	use:inview={{
		unobserveOnEnter: true
	}}
	oninview_enter={(event) => {
		if (!isInView) isInView = true;
	}}
>
	{#if isInView}
		{#await component()}
			<!-- add loader here -->
			{@render loaderFn?.()}
		{:then { default: LoadedComponent }}
			{@render Load({ ParentComponent: LoadedComponent })}
		{:catch error}
			<!-- {@debug error} -->
			<!-- add fallback error here -->
			{@render fallbackFn?.()}
		{/await}
	{/if}
</div>

{#snippet Load({ ParentComponent })}
	<ParentComponent {...comopnentProps} />
{/snippet}
