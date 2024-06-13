<script>
	import { onMount } from 'svelte';

	let svelteVersion = '';

	onMount(async () => {
		// Fetch the latest version of Svelte from the npm registry
		const response = await fetch('https://registry.npmjs.org/svelte/latest');
		const data = await response.json();
		svelteVersion = data.version;
	});

	const exampleCode = `
  &lt;script&gt;
    let count = 0;
  &lt;/script&gt;
  
  &lt;button on:click=&quot;{() => count++}&quot;&gt;
    Clicked {count} {count === 1 ? 'time' : 'times'}
  &lt;/button&gt;
    `;
</script>

<div class="container">
	<h1>About Svelte</h1>
	<p>
		Svelte is a modern front-end framework that enables developers to build highly reactive and
		efficient web applications. Unlike traditional frameworks such as React or Vue, Svelte shifts
		much of the work to compile time, resulting in faster runtime performance and smaller bundle
		sizes.
	</p>
	<p>
		When you write Svelte components, they are compiled into highly optimized vanilla JavaScript
		code that directly manipulates the DOM. This approach eliminates the need for a virtual DOM and
		reduces the amount of boilerplate code you need to write.
	</p>
	<p>
		Svelte is also known for its simplicity and ease of use. With its intuitive syntax and powerful
		features, Svelte allows you to build complex applications with less code and better
		maintainability.
	</p>
	<div class="code">
		{@html exampleCode}
	</div>
	<p class="version">
		Current Svelte Version: {svelteVersion}
	</p>
</div>

<style>
	.container {
		max-width: 800px;
		margin: 0 auto;
		padding: 20px;
	}

	h1 {
		font-size: 2.5em;
		margin-bottom: 20px;
	}

	p {
		font-size: 1.2em;
		line-height: 1.6;
		margin-bottom: 20px;
	}

	.version {
		font-size: 1em;
		color: #888;
		margin-top: 10px;
	}

	.code {
		background-color: #f5f5f5;
		color: var(--color-text-dark);
		border-left: 4px solid #6200ea;
		padding: 10px;
		font-family: monospace;
		font-size: 1em;
		overflow-x: auto;
		white-space: pre-wrap;
	}
</style>
