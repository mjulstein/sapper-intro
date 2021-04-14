<script>
  import subtopics from "./_lib/subtopics";
</script>

<h1>Components</h1>
<ul>
  {#each subtopics as { name }}
    <li>{name}</li>
  {/each}
</ul>
