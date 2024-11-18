<script>
	let { name, age, github, children } = $props();
</script>

<div>
	<h1>Hello, I'm {name}</h1>
	<p>I'm {age} years old</p>
	<p>My Github username is <a href="https://github.com/{github}">{github}</a></p>
	<div>Children: {@render children?.()}</div>
</div>
