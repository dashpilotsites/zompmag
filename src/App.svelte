<script>
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";
  import marked from "marked";
  const apiURL = "https://zompmag-nu.vercel.app/api/data.json";
  let data = [];
  data.entries = [];

  onMount(async function() {
    marked.setOptions({
      breaks: true
    });
    const response = await fetch(apiURL);
    data = await response.json();
  });
</script>

<header>
  <h1>Zompmag</h1>
</header>
<main>
  {#each data.entries as item}
    <section transition:fade>
      <div class="content">
        <h1>{item.title}</h1>
        <p>
          {@html marked(item.body)}
        </p>
      </div>
    </section>
  {/each}
</main>

<style>
  p {
    line-height: 1.5em;
  }
  h1 {
    font: 400 45px/1.5 "Playfair Display", Georgia, serif;
    margin-bottom: 20px;
  }

  main,
  p {
    font: 300 18px/1.7 "Inter", Verdana, Helvetica, sans-serif;
  }

  .content {
    max-width: 700px;
    margin: 0 auto;
  }

  header {
    text-align: center;
    padding: 50px;
  }

  header h1 {
    margin-bottom: 0;
  }

  section {
    padding: 50px;
    border-bottom: 1px solid #ddd;
  }
</style>
