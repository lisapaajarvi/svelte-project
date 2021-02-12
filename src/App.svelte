
<script>
	export let name;
	import TodoCard from './TodoCard.svelte';
	import AddTodo from "./AddTodo.svelte"

	let todolist = JSON.parse(localStorage.getItem("todolist"))
	if (todolist === null || undefined) {
    todolist = [];
	}

  //   Our field representation, let's us easily specify several inputs
  let fields = [
	{
		id: "date",
		type: "Date",
		value: "2021-02-12",
		label: "Välj datum"
	},
	{
		id: "colour",
		type: "Select",
		value: "röd",
		label: "Välj område",
		options: [
			{ label: "Rensning", value: "röd"  },
			{ label: "Sådd", value: "blå" },
			{ label: "Förberedelser", value: "lila"},
			{ label: "Plantering", value: "gul" },
			{ label: "Skörd", value: "orange" },
			{ label: "Vattning", value: "turkos" },
			{ label: "Skadedjursbekämpning", value: "svart" },
			{ label: "Gödsel", value: "rosa" },
			{ label: "Övrigt", value: "lime" },
		]	
	},
    {
      id: "title",
      type: "Input",
      value: "",
      placeholder: "Skriv uppgiftens titel",
      label: "Uppgift",
    },
    {
      id: "description",
      type: "Input",
      value: "",
      placeholder: "Skriv mer information om uppgiften",
      label: "Information",
    },
    {
      id: "time",
      type: "Select",
      value: 1,
      label: "Välj tidsenheter",
      options: [
        { label: 1, value: 1 },
        { label: 2, value: 2 },
        { label: 3, value: 3 },
		{ label: 4, value: 4 },
        { label: 5, value: 5 },
      ],
    },
  ];
  let newTodo = {};

  function handleClick(){
	  console.log("klickade ");
  } 
  function handleClick2(){
	  console.log("klickade toppen");
  } 
</script>

<main>
	<div >
		<img src="images/guinea-pig.png" alt="cute guinea pig">
		<h1 on:click={handleClick2}>Välkommen {name}!</h1>
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
	  newTodo = result;
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