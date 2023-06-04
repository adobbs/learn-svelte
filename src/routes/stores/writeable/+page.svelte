<script>
	import Decrementer from '../../../components/stores/Decrementer.svelte';
    import Incrementer from '../../../components/stores/Incrementer.svelte';
    import Resetter from '../../../components/stores/Resetter.svelte';
    import { count } from '../../../components/stores/stores.js';

	let count_value;

	count.subscribe((value) => {
		count_value = value;
	});
</script>

<h1>The count is {count_value}</h1>

<Incrementer />
<Decrementer />
<Resetter />
