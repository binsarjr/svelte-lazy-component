# Svelte Lazy Component

**Svelte Lazy Component** is a library designed for dynamically loading components in your Svelte project. It supports asynchronous component loading, passing dynamic props, and handling events effortlessly.

---

## ✨ Key Features

- **Lazy Loading**: Load components only when needed.
- **Dynamic Props**: Pass dynamic properties to lazy-loaded components.
- **Asynchronous Component Loading**: Utilize `import()` to load components asynchronously.
- **Child Content Support**: Easily include child content inside components.
- **Event Handling**: Handle events from lazy-loaded components intuitively.

---

## 📄 Basic Usage

### Import the Component
Use `LazyComponent` to load components dynamically.

```svelte
<script>
	import LazyComponent from '$lib/LazyComponent.svelte';

	let inputValue = '';
</script>

<LazyComponent
	component={() => import('$components/Input.svelte')}
	defaultValue="Lazy Loaded Value"
	onInput={(event) => {
		inputValue = event.target.value;
	}}
/>

<p>Input Value: {inputValue}</p>
```

### Pass Props and Use Child Content
You can pass props and add child content.

```svelte
<LazyComponent
	component={() => import('$components/Hello.svelte')}
	name="John Doe"
>
	<p>This is child content</p>
</LazyComponent>
```

### Render Multiple Components
Use `#each` to render multiple `LazyComponent` instances.

```svelte
<script>
	const avatars = Array.from({ length: 5 }, (_, i) => ({
		url: `https://picsum.photos/200/200?id=${i}`,
		name: `User ${i}`,
		content: `Content ${i}`,
	}));
</script>

{#each avatars as avatar}
	<LazyComponent
		component={() => import('$components/GalleryPhoto.svelte')}
		{...avatar}
	/>
{/each}
```

---

## 🔧 API

### Props
- **`component`** _(required)_: An asynchronous function to load the component (`import()`).
- **`...props`**: Properties passed to the loaded component.

### Events
- **Custom Events**: Handle events the usual way (e.g., `on:eventName`).

---

## 🔗 Example Project

Check out the implementation example on [GitHub Repository](https://github.com/binsarjr/svelte-lazy-component/blob/main/src/routes/+page.svelte).

---

## 🛠 Usage Notes
1. Currently, bindable props are not supported. Use event handlers to update values as needed.
2. The library is designed for easy lazy loading. Manage your dependencies efficiently for the best experience.

---

## 🏗 Development and Contribution

We welcome contributions to this project! Here's how you can help:

1. **Improve Documentation**: The library needs better documentation. If you have experience writing clear, user-friendly documentation, your contributions are highly appreciated!
2. **Report Bugs**: Found an issue? Let us know by opening a GitHub issue.
3. **Add Features**: Have a great idea? Fork the repository, implement your feature, and create a pull request.

<!-- For any contribution, please check the [Contributing Guide](https://github.com/binsarjr/svelte-lazy-component/blob/main/CONTRIBUTING.md). -->

---

## 📜 License

This library is released under the MIT License. Feel free to use it in your projects.

--- 

Contributions are highly appreciated! Let's make this library even better. 🚀