<script>
  import subtopics from "./_lib/subtopics";
</script>

<ul>
  {#each subtopics as { name }}
    <li>{name}</li>
  {/each}
</ul>
