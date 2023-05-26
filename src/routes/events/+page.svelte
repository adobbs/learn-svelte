<script>
	// let m = { x: 0, y: 0 };

    import Inner from "../../components/Inner.svelte";

	// function handleMove(event) {
	// 	m.x = event.clientX;
	// 	m.y = event.clientY;
	// }

    function handleMessage(event) {
		alert(event.detail.text);
	}
</script>

<h1>Events Examples</h1>
<button on:click|once={() => alert('clicked')}>
	Click me
</button>

<div>
    <Inner on:message={handleMessage} />
</div>

<!-- <div 
    on:pointermove={(e) => {
        m = {x: e.clientX, y: e.clientY};
    }}
    class="pointer"
>
	The pointer is at {m.x} x {m.y}
</div> -->

<style>
    div, button {
        margin-bottom: 1rem;
    }

	/* .pointer {
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		padding: 1rem;
	} */
</style>
