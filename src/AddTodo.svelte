<script>
    import Input from "./Input.svelte";
    import Select from "./Select.svelte";
    import Date from "./Date.svelte";
      export let onSubmit;

    // Converts fields to objects
    const fieldsToObject = (fields) =>
      fields.reduce((p, c) => ({ ...p, [c.id]: c.value }), {});

    // When submitting, turn our fields representation into a JSON body
    const handleSubmit = () => onSubmit(fieldsToObject(fields));

    //   Input fields for todolist

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
  </script>
  
  <form on:submit={handleSubmit(fields)}>
      <!-- Loop the fields and render the correct representation based on field.type -->
      {#each fields as field}
          {#if field.type === "Input"}
              <Input bind:value={field.value} id={field.id} label={field.label} placeholder={field.placeholder} />
          {:else if field.type === "Select"}
              <Select bind:value={field.value} id={field.id} label={field.label} options={field.options}/>
          {:else if field.type === "Date"}
            <Date bind:value={field.value} id={field.id} label={field.label}/>
          {/if}
      {/each}
      <button type="submit">Lägg till uppgift</button>
  </form>