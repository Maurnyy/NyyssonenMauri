<script>
  export let otsikko = 'XXX';
</script>

<!-- Propsi -->
<header>{otsikko.toUpperCase()}</header>

<style>
  header {
    text-align: center;
    font-size: 60px;
    display: flex;
    justify-content: center;
    height: 6em;
    margin-top: 20px;
    padding: 40px;
    border-radius: 30px;
    letter-spacing: 8px;
    color: rgb(0, 0, 0);
    background-image: linear-gradient(to right, #7d87741a, #e2ff0566),
      url('https://media.giphy.com/media/kZeOTMbJGYR3Kndyzc/giphy.gif');
    background-size: 50px;
    -webkit-text-stroke: 2px rgb(9, 194, 179);
    height: 50px;
  }
</style>
