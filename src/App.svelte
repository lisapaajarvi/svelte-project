<script>
	export let name;
	import TodoCard from './TodoCard.svelte';
</script>

<main>
	<div >
		<img src="images/guinea-pig.png" alt="cute guinea pig">
		<h1>Hello {name}!</h1>
	</div>


	<TodoCard>		
		<span slot="title">Rensa ogräs A5</span>
		<span slot="description">Grovrensa bland lupinerna.</span>
		<p slot="time">0/2</p>
	</TodoCard>
	<TodoCard>		
		<span slot="title">Förbereda A2</span>
		<span slot="description">Gräva och rensa bort ogräsrötter i bädd A2. 	
		</span>
		<p slot="time">1/3</p>
	</TodoCard>
</main>


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		background-color: green;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4rem;
		font-weight: 100;
	}
	h2 {
        font-size: 1.2rem;
    }
	img {
		width: 5rem;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>