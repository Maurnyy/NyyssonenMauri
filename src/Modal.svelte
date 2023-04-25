<script>
</script>

<div class="backdrop" />

<div class="modal">
  <slot />
</div>

<style>
  .backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
  }

  .modal {
    padding: 1rem;
    position: fixed;
    top: 10vh;
    left: 10vw;
    width: 60%;
    max-height: 80vh;
    overflow: scroll;
    background-image: linear-gradient(#514115, #39db18ad);
  }
</style>
