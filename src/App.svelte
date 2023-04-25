<script>
  import Painike from './Painike.svelte';
  import Arvopeli from './Arvopeli.svelte';
  import Footer from './Footer.svelte';
  import Header from './Header.svelte';
  import Pelit from './Pelit.svelte';

  let peliInfo = false;
  let lista = false;
  function naytaPeli() {
    peliInfo = true;
  }
  function listaPeleista() {
    lista = true;
  }
  const appInfo = {
    name: 'Mauri Nyyssönen',
    year: new Date().getFullYear(),
    course: 'Frontend perusteet',
    otsikko: 'Rick & Morty',
  };
  let url = 'https://www.mmobomb.com/g/433/thumbnail.jpg';
</script>

<main>
  {#if peliInfo}
    <Arvopeli on:sulje={() => (peliInfo = false)} />
  {/if}
  {#if lista}
    <Pelit on:sulje={() => (lista = false)} />
  {/if}
  <Header otsikko={appInfo.otsikko} />
  <div class="gridi">
    <div class="container-1" />
    <div class="container-2">
      <div class="teksti">
        <img src={url} alt="runescape" margin-top="10px" />
        <p>
          <a href="https://runescape.com">Runesape</a> on ainut ja oikea valinta
          MMO peliksi.
        </p>
        <p class="mauri">
          Mutta koska alkuperäinen fetch ei toiminut, niin arvotaan Rick & Morty
          hahmo.
        </p>
      </div>
      <Painike on:click={naytaPeli}>Arvo hahmo</Painike>
      <Painike on:click={listaPeleista}>Lista hahmoista</Painike>
    </div>
    <div class="container-3" />
  </div>
</main>
<Footer>&copy; {appInfo.name} {appInfo.year} - {appInfo.course}</Footer>

<style>
  .gridi {
    margin-top: 30px;
    display: grid;
    grid-template-columns: 20 60 20;
    grid-template-areas: 'container-1 container-2 container-3';
  }

  .teksti {
    background-color: #c8933d;
    padding-top: 30px;
    padding-bottom: 20px;
    margin-bottom: 20px;
  }
  main {
    text-align: center;
  }
  .mauri {
    font-size: 30px;
    color: blueviolet;
  }
</style>
