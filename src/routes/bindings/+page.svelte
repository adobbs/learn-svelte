<script>
	let name = 'world';

    let a = 1;
    let b = 2;

    let yes = false;

    let questions = [
		{
			id: 1,
			text: `Where did you go to school?`
		},
		{
			id: 2,
			text: `What is your mother's name?`
		},
		{
			id: 3,
			text: `What is another personal fact that an attacker could easily find with Google?`
		}
	];

	let selected;

	let answer = '';

	function handleSubmit() {
		alert(
			`answered question ${selected.id} (${selected.text}) with "${answer}"`
		);
	}

    let scoops = 1;
	let flavours = [];

	const formatter = new Intl.ListFormat('en', { style: 'long', type: 'conjunction' });
</script>

<h1>Bindings Examples</h1>

<h2>Example 1 - Text Inputs</h2>

<input bind:value={name} />

<h1>Hello {name}!</h1>

<h2>Example 2 - Numeric Inputs</h2>

<label>
	<input type="number" bind:value={a} min="0" max="10" />
	<input type="range" bind:value={a} min="0" max="10" />
</label>

<label>
	<input type="number" bind:value={b} min="0" max="10" />
	<input type="range" bind:value={b} min="0" max="10" />
</label>

<p>{a} + {b} = {a + b}</p>

<h2>Example 3 - Checkbox Inputs</h2>

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

<h2>Example 4 - Select controls</h2>

<h3>Insecurity questions</h3>

<form on:submit|preventDefault={handleSubmit}>
	<select
		bind:value={selected}
		on:change={() => (answer = '')}
	>
		{#each questions as question}
			<option value={question}>
				{question.text}
			</option>
		{/each}
	</select>

	<input bind:value={answer} />

	<button disabled={!answer} type="submit">
		Submit
	</button>
</form>

<p>
	selected question {selected
		? selected.id
		: '[waiting...]'}
</p>

<h2>Example 5 - Group Inputs</h2>

<h3>Size</h3>

{#each [1, 2, 3] as number}
	<label>
		<input
			type="radio"
			name="scoops"
			value={number}
            bind:group={scoops}
		/>

		{number} {number === 1 ? 'scoop' : 'scoops'}
	</label>
{/each}

<h3>Flavours</h3>

<!-- Checkboxes -->
{#each ['cookies and cream', 'mint choc chip', 'raspberry ripple'] as flavour}
	<label>
		<input
			type="checkbox"
			name="flavours"
			value={flavour}
            bind:group={flavours}
		/>

		{flavour}
	</label>
{/each}

<!-- Select Multiple -->
<select multiple bind:value={flavours}>
    {#each ['cookies and cream', 'mint choc chip', 'raspberry ripple'] as flavour}
        <option>{flavour}</option>
    {/each}
</select>

{#if flavours.length === 0}
	<p>Please select at least one flavour</p>
{:else if flavours.length > scoops}
	<p>Can't order more flavours than scoops!</p>
{:else}
	<p>
		You ordered {scoops} {scoops === 1 ? 'scoop' : 'scoops'}
		of {formatter.format(flavours)}
	</p>
{/if}

<style>
    h2 {
        margin-top: 4rem;
    }
</style>
