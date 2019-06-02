<script>
  import { onMount } from "svelte";
  import { spring } from 'svelte/motion';
  import { fade } from "svelte/transition";

  import Card from "./shared/Card.svelte";

  let top = spring(2)
  let left = spring(2)

  const move = (x, y) => {
    setTimeout(() => {
      top.set(x)
      left.set(y)
      move( Math.random() * 98,  Math.random() * 98)
    }, 500)
  }

  move(50, 50);

</script>

<style>
  .box {
    height: 100%;
    width: 100%;
    position: absolute;
    left: 0;
    top: 5px;
  }

  .ball {
    height: 20px;
    width: 20px;
    background-color: hotpink;
    position: absolute;
    border-radius: 50%;
    transform: translate(-50%, -50%);
  }
</style>

<Card title="Animaty Ball" height={200}>
  <div class="box"><div class="ball" style="top: {$top}%; left: {$left}%" /></div>
</Card>
