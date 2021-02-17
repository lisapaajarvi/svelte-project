
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
<header>
	<img src="images/guinea-pig.png" alt="cute guinea pig">
	<h1>Välkommen {name}!</h1>
</header>
<main>
	<div class="todo-container">
		{#each todolist as { date, colour, title, description, time } }	
			<TodoCard>
				<span slot="date">{date}</span>		
				<span slot="colour">{colour}</span>	
				<span slot="title">{title}</span>
				<span slot="description">{description}</span>
				<p slot="time">{time}</p>
			</TodoCard>
		{/each}
	</div>

	<div class="todo-form">
		<AddTodo
		onSubmit={(result) => {
		let newTodo = result;
		todolist.push(newTodo)
		localStorage.setItem("todolist", JSON.stringify(todolist))
		}}
		{fields} />
	</div>
  
</main>


<style>

	header {
		text-align: center;
		padding: 1rem;
		background-color: green;
	}
	main {
		padding: 1rem;
		background-color: green;
		display: flex;
		justify-content: space-around;
	}

	.todo-form {
		color: #70e91f;
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