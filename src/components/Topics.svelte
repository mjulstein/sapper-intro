<script>
  import Topic from "./Topic.svelte";
  const topics = [
    "TypeScript!?",
    "Sapper filesystem",
    "Routing",
    "Components</br>nstuff",
    "on:eventName",
    "Special Elements (self, head, ...)",
    "Syntax ($: {if/each etc})",
    "Styles",
  ];
</script>

<ul>
  {#each topics as topic}
    <Topic>
      {@html topic}
    </Topic>
  {/each}
</ul>

<style>
  ul {
    list-style: none;
  }
</style>
