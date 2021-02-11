<script>
	export let name;
	import TodoCard from 'TodoCard.svelte';
</script>

<main>
	<h1>Hello {name}!</h1>

	<TodoCard>
		<h2>Rensa ogräs</h2>
		<p>Uppskattad tid</p>
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
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>