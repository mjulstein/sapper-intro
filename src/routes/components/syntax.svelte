<script>
  import DemoButton from "./_lib/DemoButton.svelte";
  import { store } from "../../components/store";
  import EventComponent from "./_lib/EventComponent.svelte";

  let idNumber = 0;
  let text = "";
  $: disabled = !text;
  const handleClick = async () => {
    const submittedText = text;
    setTimeout(() => {
      store.set([...$store, { id: idNumber++, content: submittedText }]);
    }, Math.random() * 5000);
    text = "";
  };
  const handleKeyDown = ({ key }) => {
    if (key === "Enter") {
      handleClick();
    }
  };
  const removeItem = (i) => {
    let textsCopy = $store.filter(({ id }) => i !== id);
    store.set(textsCopy);
  };
  let promise;
  const runasyncTask = () => {
    promise = new Promise((resolve) => {
      setTimeout(() => {
        resolve("WORLD");
      }, Math.random() * 5000);
    });
  };
  let verticalScroll;
  let textAreaHeight;
</script>

<h2>Syntax</h2>
<input type="text" bind:value={text} />
<DemoButton {disabled} on:click={handleClick}>Clear text</DemoButton>
<ul>
  {#each $store as { id, content }, i (id)}
    <li on:click={() => removeItem(id)}>
      element {i} = {id} : {content}
      <EventComponent {id} on:div-click={({ detail }) => alert(detail.id)} />
    </li>
  {/each}
</ul>
<textarea
  bind:clientHeight={textAreaHeight}
  rows={Math.floor(textAreaHeight) / 20}
/>
<button on:click={runasyncTask}>Run async</button>
<p>
  Hello
  {#await promise}
    Loading....
  {:then value}
    {value}
  {/await}
  VerticalScroll = {verticalScroll}px;
</p>

<svelte:window on:keydown={handleKeyDown} bind:scrollY={verticalScroll} />

<style>
  textarea {
    display: block;
  }
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
  ul > li {
    border: solid black 1px;
  }
</style>
