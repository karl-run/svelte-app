<script>
  import Header from "./Header.svelte";
  import SomeContent from "./SomeContent.svelte";
  import FetchedContent from "./FetchedContent.svelte";
</script>

<style>
  .content {
    display: flex;
    flex-wrap: wrap;
  }
</style>

<Header />
<div class="content">
  <SomeContent />
  <FetchedContent />
</div>
