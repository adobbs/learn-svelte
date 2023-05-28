<script>
	let name = 'world';

    let a = 1;
    let b = 2;

    let yes = false;
</script>

<h1>Bindings Examples</h1>

<h2>Example 1</h2>

<input bind:value={name} />

<h1>Hello {name}!</h1>

<h2>Example 2</h2>

<label>
	<input type="number" bind:value={a} min="0" max="10" />
	<input type="range" bind:value={a} min="0" max="10" />
</label>

<label>
	<input type="number" bind:value={b} min="0" max="10" />
	<input type="range" bind:value={b} min="0" max="10" />
</label>

<p>{a} + {b} = {a + b}</p>

<h2>Example 3</h2>

<label>
	<input type="checkbox" bind:checked={yes} />
	Yes! Send me regular email spam
</label>

{#if yes}
	<p>
		Thank you. We will bombard your inbox and sell
		your personal details.
	</p>
{:else}
	<p>
		You must opt in to continue. If you're not
		paying, you're the product.
	</p>
{/if}

<button disabled={!yes}>Subscribe</button>

<style>
    h2 {
        margin-top: 4rem;
    }
</style>
