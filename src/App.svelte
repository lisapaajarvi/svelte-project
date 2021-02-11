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
		<h2 slot="title">Rensa ogräs</h2>
		<p slot="task">Uppskattad tid: 1 timme</p>
	</TodoCard>
	<TodoCard>		
		<h2 slot="title">Förbereda bädd A2</h2>
		<p slot="task">Uppskattad tid: 3 timmar</p>
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