<script lang="ts">
	interface Emojis {
        apple: string;
        banana: string;
        carrot: string;
        doughnut: string;
        egg: string;
    }

    const emojis: Emojis = {
		apple: '🍎',
		banana: '🍌',
		carrot: '🥕',
		doughnut: '🍩',
		egg: '🥚'
	};

	// the name is updated whenever the prop value changes...
	export let name: keyof Emojis;

	// ...but the "emoji" variable is fixed upon initialisation
	// of the component because it uses `const` instead of `$:`
	const emoji = emojis[name];
</script>

<p>{emoji} = {name}</p>
