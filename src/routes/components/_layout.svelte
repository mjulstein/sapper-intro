<script context="module">
  export async function preload({ path }) {
    return { path };
  }
</script>

<script>
  import TopicNav from "./_lib/TopicNav.svelte";
  export let path = "";
  export let segment;
</script>

<style>
  section {
    display: flex;
    flex-wrap: wrap;
  }
  section > article {
    flex: 1;
  }
  h1 {
    width: 100%;
  }
</style>

<svelte:head>
  <title>Components</title>
</svelte:head>
<section>
  <h1>Components</h1>
  {#key segment}
    <TopicNav {path} selected={segment} />
  {/key}
  <article>
    <slot />
  </article>
</section>
