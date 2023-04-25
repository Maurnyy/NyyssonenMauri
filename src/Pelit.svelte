<script>
  import { onMount } from 'svelte';
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let close = 'Close';

  import Modal from './Modal.svelte';
  import Painike from './Painike.svelte';

  function sulje() {
    dispatch('sulje');
  }
  const getGames = async () => {
    const response = await fetch('https://rickandmortyapi.com/api/character/');
    if (!response.ok) {
      throw new Error('Cannot fetch data.');
    }
    let data = await response.json();

    return data;
  };
  onMount(async () => {
    getGames();
  });
</script>

<Modal>
  <div class="painike">
    <Painike on:click={sulje}>{close}</Painike>
  </div>
  {#await getGames()}
    <p>...Lataa</p>
  {:then peli}
    {#each peli.results as x}
      <div class="hahmo">
        <p class="mauri">{x.name}</p>
        <img src={x.image} alt="digimon" />
      </div>
    {/each}
  {:catch error}
    <p>Virhe havaittu!</p>
  {/await}
</Modal>

<style>
  .painike {
    position: fixed;
    bottom: 6vh;
    right: 10vw;
  }
  .hahmo {
    box-shadow: 2px solid rgb(red, green, blue);
    border-top: 8px solid rgb(0, 255, 145);
    border-bottom: 8px solid rgb(0, 255, 145);
    border-right: 8px solid rgb(255, 0, 251);
    border-left: 8px solid rgb(255, 0, 251);
  }
  .mauri {
    font-size: 20px;
    color: rgb(37, 204, 193);
  }
</style>
