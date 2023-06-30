<script>
  import { writable } from 'svelte/store';
  const progress = writable(0);
  
  // import { tweened } from 'svelte/motion';
  // import { cubicOut } from 'svelte/easing';

  // const progress = tweened(0, {
  //   duration: 400,
  //   easing: cubicOut
  // });  
  
</script>

<progress  value={$progress}/>

<button on:click={() => progress.set(0)}>
  0%
</button>

<button on:click={() => progress.set(0.25)}>
  25%
</button>

<button on:click={() => progress.set(0.5)}>
  50%
</button>

<button on:click={() => progress.set(0.75)}>
  75%
</button>

<button on:click={() => progress.set(1)}>
  100%
</button>

<div>
  <p>if i uncomment the svelte solution copied from the svelte tutorial site ( tweens.svelte component ), the app breaks and throws...</p>
  <code>TypeError: Cannot read properties of undefined (reading 'writable')</code>
  <p>i was in the middle of creating a FAQ component and tried to use tween and easing and i couldn't make it to work here... but works okay in the svelte REPL...</p>
</div>

<style>
  progress {
    display: block;
    width: 100%;
  }
</style>
