<script>
  import subtopics from "./subtopics";
  export let path;
</script>

<aside>
  <ul>
    {#each subtopics as { route, name }, i}
      <li><a href="{path}/{route}">{i + 1}: {name}</a></li>
    {/each}
  </ul>
</aside>

<style>
  aside {
    width: 20rem;
  }
  ul {
    list-style: none;
  }
  li,
  ul {
    margin: 0;
    padding: 0;
  }
  a {
    display: block;
    text-decoration: none;
    padding: 1rem;
  }
  a:hover {
    text-decoration: underline;
    color: #a70000;
    background-color: lightcoral;
  }
</style>
