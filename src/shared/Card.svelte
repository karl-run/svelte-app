<script>
  export let title;
  export let height;
</script>

<style>
  .card {
    flex: 1 1 450px;
    border-radius: 2px;
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3);
    padding: 1em;
    margin: 16px;
    min-width: 300px;
    position: relative;
  }

  h3 {
    margin-top: 0;
  }
</style>

<div class="card" style="height: {height}px">
  {#if title}
    <h3>{title}</h3>
  {/if}
  <slot />
</div>
