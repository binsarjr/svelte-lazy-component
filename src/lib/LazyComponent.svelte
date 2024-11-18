<script>
	import { inview } from 'svelte-inview';

	let { component, children, loaderFn, fallbackFn, ...comopnentProps } = $props();

	let isInView = $state(false);
</script>

<div
	use:inview
	oninview_enter={(event) => {
		if (!isInView) isInView = true;
	}}
>
	{#if isInView}
		{#await component()}
			<!-- add loader here -->
			{@render loaderFn?.()}
		{:then { default: LoadedComponent }}
			{@render Load({ children, ParentComponent: LoadedComponent })}
		{:catch error}
			<!-- {@debug error} -->
			<!-- add fallback error here -->
			{@render fallbackFn?.()}
		{/await}
	{/if}
</div>

{#snippet Load({ children, ParentComponent })}
	<ParentComponent {...comopnentProps}>
		{@render children?.()}
	</ParentComponent>
{/snippet}
