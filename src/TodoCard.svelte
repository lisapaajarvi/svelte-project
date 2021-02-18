<script>
</script>
<style>
    *  {
        box-sizing: border-box;
    }
	.todo {
		width: 400px;
		border: 3px solid white;
		border-radius: 10px;
		box-shadow: 2px 2px 8px black;
		padding: 1rem;
		margin: 1rem;
        background-color: lightgreen;
        text-align: left;
        position: relative;
	}
    .title-div {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }
    .color {
        width: 2rem;
        height: 2rem;
        border: .2rem solid white;
        border-radius: .2rem;
        background-color: red;
    }
    .time-est {
        width: 2rem;
        height: 2rem;
        position: absolute;
        bottom: 1rem;
        right: 1rem;
        border-radius: .2rem;
        text-align: center;
        font-weight: bold;
    }
    button {
        height: 2rem;
        width: 2rem;
        border-radius: .2rem;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 0;
    }

</style>

<div class="todo">
    <div class="title-div">
        <div class="color"><slot name="color"></slot></div>
        <h2><slot name="title"></slot></h2>
        <button>X</button>
    </div>
	<p><slot name="description"></slot></p>
    <p><slot name="date"></slot></p>
    <div class="time-est">
        <slot name="time"></slot>
    </div>
</div>