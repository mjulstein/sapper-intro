<script>
  const subtopics = [
    "File locations",
    "Special Files",
    "Prefixes",
    "Brackets",
    "Routing",
  ];
</script>

<svelte:head>
  <title>Sapper filesystem</title>
</svelte:head>
<section>
  <h1>Sapper filesystem</h1>
  <ul>
    {#each subtopics as topic}
      <li>{topic}</li>
    {/each}
  </ul>
</section>
