<script>
  import { createEventDispatcher } from "svelte";
  export let id;
  const dispatch = createEventDispatcher();
</script>

<div on:click|stopPropagation={() => dispatch("div-click", { id })}>Click</div>
