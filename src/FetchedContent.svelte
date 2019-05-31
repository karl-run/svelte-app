<script>
  import { onMount } from "svelte";
  import { spring } from 'svelte/motion';
  import { fade } from "svelte/transition";

  import Card from "./shared/Card.svelte";

  let height = spring(60)

  let items;

  const URL = "https://node.gql.systek.dev";
  const query = `
  query {
    ingredients {
      id
      name
    }
  }`;

  onMount(async () => {
    const response = await fetch(URL, {
      method: "POST",
      headers: {
        accept: "*/*",
        "content-type": "application/json"
      },
      body: JSON.stringify({
        operationName: null,
        variables: {},
        query
      })
    });
    const result = await response.json();

    items = result.data.ingredients;
    height.set(60 + (items.length * 17))
  });
</script>

<style>

</style>

<Card title="Dynamic content" height={$height}>
  {#if !items}
    <div>Loading..</div>
  {:else}
    <div>
      {#each items as ingredient, index (ingredient.id)}
        <div transition:fade={{ delay: index * 100 }}>{ingredient.name}</div>
      {/each}
    </div>
  {/if}
</Card>
