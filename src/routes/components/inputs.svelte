<script>
  let textInput = "";
  let textArea = "";

  let checkItems = ["first", "second", "third", "fourth", "fifth"];
  let checked = [];
  let radioSelection;
  function join(item) {
    if (item.length === 1) return item[0];
    return `${item.slice(0, -1).join(", ")} and ${item[item.length - 1]}`;
  }
</script>

<style>
  .radio,
  .checkbox {
    display: block;
    padding: 0.1rem;
  }
  .radio-select p > span {
    text-decoration: underline blue;
  }
</style>

<h2>Inputs</h2>

<div class="checkbox-select">
  <p>
    Checkboxes can populate an array of values by binding them to the same
    group:
  </p>
  {#each checkItems as item}
    <span class="checkbox">
      <input
        type="checkbox"
        bind:group={checked}
        value={item}
        id="{item}_checker" /><label for="{item}_checker">{item}</label>
    </span>
  {/each}
  {#if checked.length}
    <p>The checked items are: {join(checked)}</p>
  {/if}
</div>

<div class="radio-select">
  <p>Radiobuttons can change a single value binding them to the same group:</p>
  {#each checkItems as item}
    <span class="radio">
      <input
        type="radio"
        bind:group={radioSelection}
        value={item}
        id="{item}_radio" /><label for="{item}_radio">{item}</label>
    </span>
  {/each}
  {#if radioSelection}
    <p>Currently selected the <span>{radioSelection}</span> option</p>
  {/if}
</div>
