<script>
  import { onMount } from 'svelte';
  import { createEventDispatcher } from 'svelte';
  import Modal from './Modal.svelte';
  import Painike from './Painike.svelte';
  import { fade, fly } from 'svelte/transition';

  const dispatch = createEventDispatcher();
  export let close = 'Sulje';
  function sulje() {
    dispatch('sulje');
  }

  const getGames = async () => {
    const response = await fetch('https://rickandmortyapi.com/api/character/');
    if (!response.ok) {
      throw new Error('Cannot fetch data.');
    }
    let data = await response.json();

    arvottuLuku = Math.floor(Math.random() * (data.results.length - 1) + 1);

    return data;
  };

  onMount(async () => {
    getGames();
  });
  let arvottuLuku;
</script>

<Modal>
  {#await getGames()}
    <p>...Lataa</p>
  {:then games}
    <h1>{games.results[arvottuLuku].name}</h1>
    <img
      in:fly={{ duration: 4000, x: 0, y: -500 }}
      out:fade
      src={games.results[arvottuLuku].image}
      alt="Pelit"
    />
  {/await}
  <div class="painike">
    <Painike on:click={sulje}>{close}</Painike>
  </div>
</Modal>

<style>
  .painike {
    position: absolute;
    bottom: 2vh;
    right: 3vw;
  }
  h1 {
    font-size: 50px;
    color: rgb(37, 204, 193);
  }
  p {
    font-size: 20px;
    color: rgb(255, 173, 222);
  }
</style>
