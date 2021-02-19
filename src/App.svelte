
<script>
	export let name;
	import TodoCard from './TodoCard.svelte';
	import TodoForm from "./TodoForm.svelte"

	let todolist = JSON.parse(localStorage.getItem("todolist"))
	if (todolist === null || undefined) {
    todolist = [{"date":"2021-03-05","color":"yellow","title":"Gräva bädd A2","description":"Gräva upp bädd som har varit täckt sedan okt -20","time":2},{"date":"2021-04-04","color":"blue","title":"Så bädd A5","description":"Så bondbönor, 2 rader, avstånd 10 cm","time":2}];
	}
</script>

<header>
	<img src="images/guinea-pig.png" alt="cute guinea pig">
	<h1>Välkommen {name}!</h1>
</header>
<main>
	<div class="todo-container">
		{#each todolist as item}	
			<TodoCard {item}>
				<span slot="date">{item.date}</span>		
				<span slot="title">{item.title}</span>
				<span slot="description">{item.description}</span>
				<p slot="time">{item.time}</p>
			</TodoCard>
		{/each}
	</div>

	<div class="todo-form">
		<TodoForm
		onSubmit={(result) => {
		let newTodo = result;
		todolist.push(newTodo)
		localStorage.setItem("todolist", JSON.stringify(todolist))
		}}
		/>
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
		height: 100%;
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