<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let label;
  export let value;
  export let position;
</script>

<button
  style="grid-area: {position}"
  on:click={() => {
    dispatch("click", { value });
  }}
>
  {label}
</button>

<style>
  button {
    border: none;
    background-color: rgb(35, 35, 37);
    color: white;
    margin: 0;
    padding: 0;
    border-radius: 0;
    transition: all 100ms;
    font-size: 1.5rem;
    font-weight: 500;
    /* user-select: none; */
    -webkit-user-select: none;
    -moz-user-select: none;
  }

  button:hover {
    background-color: rgb(49, 49, 52);
    box-shadow: 0px 0px 10px 1px rgba(0, 0, 0, 0.375);
    z-index: 2;
  }

  button:active {
    background-color: rgb(45, 45, 47);
  }
</style>
