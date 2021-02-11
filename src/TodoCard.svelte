<script>

import App from "./App.svelte";

</script>
<style>
	.todo {
		width: 300px;
		border: 3px solid white;
		border-radius: 10px;
		box-shadow: 2px 2px 8px black;
		padding: 1rem;
		margin: 1rem;
        background-color: lightgreen;
	}
    .title-div {
        display: flex;
        flex-direction: row;
        justify-content: start;
    }
    img {
        height: 4rem;
        margin: 0 1rem;
    }

</style>

<div class="todo">
    <div class="title-div">
        <img src= 'images/guinea-pig.png' alt="cute guinea pig">
        <slot name="title"></slot>
    </div>
	<slot name="task"></slot>
</div>