<script>
  import { onMount } from "svelte";
  import marked from "marked";
  const apiURL = "https://zompmag-nu.vercel.app/api/data.json";
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
        {@html marked(item.body)}
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
