<script>
	let m = { x: 0, y: 0 };

	// function handleMove(event) {
	// 	m.x = event.clientX;
	// 	m.y = event.clientY;
	// }
</script>

<h1>Events Examples</h1>
<button on:click|once={() => alert('clicked')}>
	Click me
</button>

<!-- <div 
    on:pointermove={(e) => {
        m = {x: e.clientX, y: e.clientY};
    }}
    class="pointer"
>
	The pointer is at {m.x} x {m.y}
</div> -->

<style>
	.pointer {
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		padding: 1rem;
	}
</style>
