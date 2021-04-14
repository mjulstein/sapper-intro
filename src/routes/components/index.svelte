<script>
  import { fade } from "svelte/transition";
  import markupExample from "./_lib/markup-example";
  let showComponent = false;
  const text = "component";
</script>

<style>
  div {
    background-color: pink;
  }
  span {
    font-weight: bold;
  }
</style>

<h2>General</h2>
<p>
  Components in Svelte are defined by adding the file extension .svelte.<br />
  They have a structure similar to this:
</p>
<pre>
  <code>{markupExample}</code>
</pre>
{#if !showComponent}
  <button on:click={() => (showComponent = true)} transition:fade>Click the
    button to show the resulting component</button>
{/if}
{#if showComponent}
  <div>Your first <span>{text}</span></div>
{/if}
