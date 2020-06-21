<script>
  import { onMount } from "svelte";
  import snarkdown from "snarkdown";
  const apiURL = "api/data.json";
  let data = [];

  onMount(async function() {
    const response = await fetch(apiURL);
    data = await response.json();
  });
</script>

<main>
  {#each data.entries as item}
    <section>
      <h1>{item.title}</h1>
      <p>
        {@html snarkdown(item.body)}
      </p>
    </section>
  {/each}
</main>

<style>
  main {
    max-width: 600px;
    margin: 0 auto;
  }
</style>
