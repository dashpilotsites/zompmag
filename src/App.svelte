<script>
  import { onMount } from "svelte";
  const apiURL = "api/data.json";
  let data = [];

  onMount(async function() {
    const response = await fetch(apiURL);
    data = await response.json();
  });
</script>

<main>
  {#each data.entries as item}
    <div>
      <h1>{item.title}</h1>
      <p>
        {@html item.body}
      </p>
    </div>
  {/each}
</main>

<style>
  main {
    max-width: 600px;
    margin: 0 auto;
  }
</style>
