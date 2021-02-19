<script>
  import Input from "./Input.svelte";
  import Select from "./Select.svelte";
  import Date from "./Date.svelte";
  export let onSubmit;

  let fields = [
	{
		id: "date",
		type: "Date",
		value: "2021-02-18",
		label: "Välj datum"
	},
	{
		id: "color",
		type: "Select",
		value: "red",
		label: "Välj område",
		options: [
			{ label: "Rensning", value: "red"  },
			{ label: "Sådd", value: "blue" },
			{ label: "Förberedelser", value: "yellow"},
			{ label: "Plantering", value: "orange" },
			{ label: "Skörd", value: "pink" },
			{ label: "Vattning", value: "lime" },
			{ label: "Skadedjursbekämpning", value: "black" },
			{ label: "Gödsel", value: "purple" },
			{ label: "Övrigt", value: "teal" },
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
      placeholder: "Beskrivning av uppgiften",
      label: "Beskrivning",
    },
    {
      id: "time",
      type: "Select",
      value: 1,
      label: "Välj tidsenheter (30 min)",
      options: [
        { label: 1, value: 1 },
        { label: 2, value: 2 },
        { label: 3, value: 3 },
		    { label: 4, value: 4 },
        { label: 5, value: 5 },
      ],
    },
  ];

      // Converts fields to objects
    const fieldsToObject = (fields) =>
    fields.reduce((p, c) => ({ ...p, [c.id]: c.value }), {});

    const handleSubmit = () => onSubmit(fieldsToObject(fields));

  </script>
  
  <form on:submit={handleSubmit(fields)}>
    {#each fields as field}
      {#if field.type === "Input"}
        <Input bind:value={field.value} id={field.id} label={field.label} 
        placeholder={field.placeholder} />

        {:else if field.type === "Select"}
          <Select bind:value={field.value} id={field.id} label={field.label} 
          options={field.options}/>

        {:else if field.type === "Date"}
          <Date bind:value={field.value} id={field.id} label={field.label}/>
      {/if}
    {/each}
    <button type="submit">Lägg till uppgift</button>
  </form>