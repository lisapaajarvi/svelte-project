<script>
    export let value;
    export let placeholder;
    export let label;
    export let id;
  </script>
  
  <label for={id}>{label}</label>
  <input bind:value {placeholder} {id} type="text" />

  <style>
    input {
      margin: .5rem;
    }
  </style>