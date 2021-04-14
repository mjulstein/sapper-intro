<script>
  import { fade } from "svelte/transition";
  import ComponentA from "./_lib/ComponentA.svelte";
  import ComponentB from "./_lib/ComponentB.svelte";
  const pageTitle = "Components - Special Elements";
  let scrolledY;
  let locationString = "inside";
  const handleMouseenter = () => {
    locationString = "inside";
  };
  const handleMouseleave = () => {
    locationString = "outside";
  };
  let clone = false;

  const componentRefs = [
    {
      name: "compA",
      component: ComponentA,
    },
    { name: "compB", component: ComponentB },
  ];
  let selectedComponent = componentRefs[0];
</script>

<style>
  div {
    min-height: 60vh;
    padding-top: 100%;
    box-sizing: border-box;
  }
</style>

<h2>Special Elements</h2>
<p>
  Svelte comes with a few spacial elements.<br />
  They are prefixed with
  <code>svelte:</code>
  <br />
  Depending on what you want to achieve;
  <br />
  recursion, refering to a component in code or the amount of pixels the client
  has scrolled,<br />
  the special elements can help you.
</p>

<p>
  For more about the special components,
  <a href="https://svelte.dev/examples" target="_blank">good examples can be
    found on the official svelte website.</a>
</p>
<p>
  Use svelte:body to check for mouseenter and mouseleave events<br />we know
  that the clients cursor is
  {locationString}
  the document.
</p>
<article>
  <p>
    By using the svelte:component element you can refer to compoents in code.<br />
    Useful when you want to switch which compoent to show depending on a state.<br />
    Example:
  </p>
  <select bind:value={selectedComponent}>
    {#each componentRefs as option}
      <option value={option}>{option.name}</option>
    {/each}
  </select>
  <svelte:component this={selectedComponent.component} />
</article>
<div>
  <p>
    By binding the scrollY property from the body using svelte:body,<br />
    we know that this page has been scrolled
    {Math.floor(scrolledY)}
    pixels from the top.
  </p>
</div>
{#if !clone}
  <p transition:fade|local>
    By using svelte:self we can put this page inside itself ( useful for
    recursion )<br />
    Be careful to make some conditions for this to happen, for example pressing
    the button below
    <br />
  </p>
  <button on:click={() => (clone = true)} transition:fade|local>
    Put a copy of this page on the bottom of this page.
  </button>
{:else}
  <hr />
  <svelte:self />
{/if}
<svelte:window bind:scrollY={scrolledY} />
<svelte:head>
  <title>{pageTitle}</title>
</svelte:head>

<svelte:body
  on:mouseenter={handleMouseenter}
  on:mouseleave={handleMouseleave} />
