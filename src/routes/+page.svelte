<script>
    import Nested from "./Nested.svelte";

    let name = 'Svelte';
    let src = './rickroll.gif';
    let string = `this string contains some <strong>HTML!!!</strong>`;
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<p>This is a paragraph.</p>
<Nested />
<p>{@html string}</p>
<img src={src} alt="A man dances." />

<style>
    p {
        color: goldenrod;
        font-family:'Comic Sans MS', cursive;
        font-size: 2em;
    }
</style>
