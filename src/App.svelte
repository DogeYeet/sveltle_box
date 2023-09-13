<!--
set X, Y origin of the box
Three functions denote the state of the mouse 
Variable trigger used for indicating whether the mouse cursor is clicked on the box
-->
<script>
	let origin_x = 0;
	let origin_y = 0;
	var trigger = false;
	//mouse cursor is clicked onto the box
	function begin_to_move() {
		trigger = true;
	}
	//set the coordinates of the box to the new position based on the distance that the mouse travels
	//event.movementX returns the distance the mouse travels in X coordinate 
	//event.movemntY returns the disrance the mouse travels in Y coordinate
	function moving(event) {
		if(trigger) {
			origin_x += event.movementX;
			origin_y += event.movementY;
		}
	}
	//mouse is released
	function stop() {
		trigger = false;
	}
</script>

<!--
	set box position to absolute to allow the box to be placed in anywhere
	set color of the box to black
	set the dimension of the box
-->
<style>
	.box {
		position: absolute;
		background-color: black;
		height:60px;
		width:60px;
	}
</style>

<!--EventLisnters for mouse being clicked, moving, and released
svelte:window makes the mouse movement only takes place in the svelte window
-->
<h1 on:mousedown={begin_to_move} style="left: {origin_x}px; top: {origin_y}px;" class="box"  on:mouseup={stop} >
</h1>
<svelte:window on:mousemove={moving}></svelte:window>
