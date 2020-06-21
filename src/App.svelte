<script>
  import { onMount } from "svelte";
  const apiURL = "api/data.json";
  let data = [];

  onMount(async function() {
    const response = await fetch(apiURL);
    data = await response.json();
  });
</script>

<style>

</style>

<main>
  {#each data.entries as item}
    <div>
      <p>{item.title}</p>
    </div>
  {/each}
</main>
