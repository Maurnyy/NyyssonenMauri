<script>
  import { fade, slide } from 'svelte/transition';
</script>

<button in:slide={{ duration: 3000, x: 0, y: 400 }} out:fade on:click>
  <slot /></button
>

<style>
  button {
    background-color: rgb(45, 66, 66);
    border: 8px dashed rgb(0, 224, 202);
    border-radius: 20px;
    padding: 0.5em;
    width: 10em;
    color: rgb(0, 224, 202);
    font-family: fantasy;
    font-size: 30px;
    margin: 0.5em;
  }
</style>
