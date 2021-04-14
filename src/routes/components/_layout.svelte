<script context="module">
  export async function preload({ path }) {
    return { path };
  }
</script>

<script>
  import TopicNav from "./_lib/TopicNav.svelte";
  export let path = "";
</script>

<svelte:head>
  <title>Components</title>
</svelte:head>
<section>
  <TopicNav {path} />
  <article>
    <slot />
  </article>
</section>
