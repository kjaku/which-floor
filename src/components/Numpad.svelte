<script>
  export let handleClick;
  const keys = [1, 2, 3, 4, 5, 6, 7, 8, 9, '<', 0, '>'];
</script>

<main>
  {#each keys as key, i}
    <button on:click={handleClick(key)} class="key" {i}>{key}</button>
  {/each}
</main>

<style>
  main {
    display: grid;
    grid-gap: 5px;
    grid-template-columns: 1fr 1fr 1fr;
  }
  button {
    background-color: transparent;
  }
  .key {
    text-align: center;
    border: 3px solid gray;
    border-radius: 10px;
    font-size: 5vh;
    line-height: 8vh;
  }
</style>
