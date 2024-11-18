<script>
	let { children, ok } = $props();
</script>

<p>Hello world {ok}</p>
{@render children?.()}
