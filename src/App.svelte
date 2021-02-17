
<script>
	export let name;
	import TodoCard from './TodoCard.svelte';
	import AddTodo from "./AddTodo.svelte"
	import fields from "./AddTodo.svelte"

	let todolist = JSON.parse(localStorage.getItem("todolist"))
	if (todolist === null || undefined) {
    todolist = [];
	}

</script>

<main>
	<div >
		<img src="images/guinea-pig.png" alt="cute guinea pig">
		<h1>Välkommen {name}!</h1>
	</div>

	{#each todolist as { date, colour, title, description, time } }	
		<TodoCard>
			<span slot="date">{date}</span>		
			<span slot="colour">{colour}</span>	
			<span slot="title">{title}</span>
			<span slot="description">{description}</span>
			<p slot="time">{time}</p>
		</TodoCard>
	{/each}

	<AddTodo
	onSubmit={(result) => {
	  let newTodo = result;
	  todolist.push(newTodo)
	  localStorage.setItem("todolist", JSON.stringify(todolist))
	}}
	{fields} />
  

</main>


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		background-color: green;
	}
	
	h1 {
		color: #70e91f;
		font-size: 4rem;
		font-weight: 100;
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