<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  import Painike from './Painike.svelte';
  export let laji;
  export let haku;
  export let nimi;
  export let kuvaus;
  export let omistaja;

  const tapahtumaPoista = () => dispatch('poista', nimi);
</script>

<article>
  <header>
    <h2>{laji} {nimi}</h2>
    <p class="omistaja">{omistaja}</p>
  </header>
  <img src="https://loremflickr.com/320/240/${haku}" alt="el catto" />
  <p>{kuvaus}</p>
  <footer>
    <Painike on:click={tapahtumaPoista}>Poista</Painike>
  </footer>
</article>

<style>
  article {
    background-color: #eeeeee;
    border: 1px solid black;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.5);
    margin-bottom: 3rem;
  }
  .omistaja {
    font-size: 0.8rem;
  }
</style>
