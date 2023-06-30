<script>
  import { tweened } from 'svelte/motion';
  import { cubicOut } from 'svelte/easing';

  const progress = tweened(0, {
    duration: 400,
    easing: cubicOut
  });
</script>


<button on:click={() => progress.set(300)}>
  open panel
</button>
<div class="panel" style="height: {$progress}px">
  <p>
    yey! i am the panel
  </p>
  <button on:click={() => progress.set(0)}>
  close panel
</button>
</div>

<style>
  .panel {
    color: crimson;
    width: 200px;
    background-color: aliceblue;
    overflow: hidden;
    height: 0;
  }   
</style>