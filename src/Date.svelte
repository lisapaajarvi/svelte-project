<script>
    export let value;
    export let label;
    export let id;
</script>
  
<label for={id}>{label}</label>
<input bind:value {id} type="date" />

<style>
    input {
        margin: 0.5rem;
    }
</style>