<script>
    import Nested from "./Nested.svelte";
    import PackageInfo from './PackageInfo.svelte';

	const pkg = {
		name: 'svelte',
		speed: 'blazing',
		version: 3,
		website: 'https://svelte.dev'
	};

    let name = 'Svelte';
    let src = './rickroll.gif';
    let string = `this string contains some <strong>HTML!!!</strong>`;

    let count = 0;
    $: doubled = count * 2;

    $: if (count >= 10) {
        alert('Count is dangerously high!');
        count = 0;
    }

    function increment() {
        count += 1;
    }

    let numbers = [1, 2, 3, 4];

	function addNumber() {
		// numbers.push(numbers.length + 1);
        numbers = [...numbers, numbers.length + 1];
	}

	$: sum = numbers.reduce((t, n) => t + n, 0);
</script>

<p>{numbers.join(' + ')} = {sum}</p>

<button on:click={addNumber}>
	Add a number
</button>

<h1>Hello {name.toUpperCase()}!</h1>
<div>
    <button on:click={increment}>
        Clicked {count}
        {count === 1 ? 'time' : 'times'}
    </button>
</div>
<p>{count} doubled is {doubled}</p>
{#if count > 5}
    <p>{count} is greater than 5</p>
{:else if count < 3}
    <p>{count} is less than 3</p>
{:else}
    <p>{count} is between 3 and 5, inclusive</p>
{/if}



<p>This is a paragraph.</p>
<Nested answer={42} />
<Nested />
<PackageInfo {...pkg} />
<p>{@html string}</p>
<img src={src} alt="A man dances." />

<style>
    p {
        color: goldenrod;
        font-family:'Comic Sans MS', cursive;
        font-size: 2em;
    }
</style>
