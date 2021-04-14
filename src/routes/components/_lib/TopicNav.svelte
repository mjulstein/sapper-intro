<script>
  import subtopics from "./subtopics";
  import { fly } from "svelte/transition";
  export let path;
  export let selected = null;
  $: expanded = !selected;
</script>

<style>
  button {
    position: absolute;
    display: flex;
    justify-content: center;
    transform: all 0.2 ease-out;
  }
  button > h2 {
    margin: 0;
    padding: 0.5rem;
  }
  aside {
    position: absolute;
    top: 5rem;
    background-color: azure;
    border-radius: 4px;
    border: 1px solid rgb(255, 73, 73);
  }
  ul {
    list-style: none;
  }
  li,
  ul {
    margin: 0;
    padding: 0;
  }

  .current,
  a {
    display: block;
    text-decoration: none;
    padding: 0.5rem;
  }

  .current,
  a:focus,
  a:hover {
    color: #a70000;
    background-color: lightcoral;
  }
  a:focus > span,
  a:hover > span {
    text-decoration: underline;
  }
  .current {
    cursor: default;
  }
</style>

<button on:click={() => (expanded = !expanded)}>
  <h2>Topics</h2>
</button>
{#if expanded}
  <aside transition:fly|local={{ x: -200 }}>
    <ul>
      {#each subtopics as { route, name }, i}
        <li>
          {#if selected == route}
            <span class="current">{i + 1}: <span>{name}</span></span>
          {:else}
            <a
              href={!route ? path : `${path}/${route}`}
              on:click={() => {
                selected = null;
              }}>{i + 1}:
              <span>{name}</span></a>
          {/if}
        </li>
      {/each}
    </ul>
  </aside>
{/if}
