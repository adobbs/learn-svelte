<script>
    let name = 'Svelte';
    let src = './rickroll.gif';
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<p>This is a paragraph.</p>
<img src={src} alt="A man dances." />

<style>
    p {
        color: goldenrod;
        font-family:'Comic Sans MS', cursive;
        font-size: 2em;
    }
</style>
