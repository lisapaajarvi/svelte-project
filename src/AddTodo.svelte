<script>
    import Input from "./Input.svelte";
    import Select from "./Select.svelte";
    import Date from "./Date.svelte";
    export let onSubmit;
    export let fields;

    // Converts fields to objects
    const fieldsToObject = (fields) =>
      fields.reduce((p, c) => ({ ...p, [c.id]: c.value }), {});

    // When submitting, turn our fields representation into a JSON body
    const handleSubmit = () => onSubmit(fieldsToObject(fields));

  </script>
  
  <style>
    :global(input, select) {
      margin: 5px;
    }
  </style>
  
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