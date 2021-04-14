<script>
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<header>
  <Nav {segment} />
</header>

<main>
  <slot />
</main>

<style>
  main {
    position: relative;
    max-width: 56em;
    background-color: white;
    padding: 2em;
    margin: 0 auto;
    box-sizing: border-box;
  }
  main > :global(section > h1) {
    text-align: center;
    text-transform: uppercase;
    margin: 0 0 0.5em 0;
  }
</style>
