<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  import Modal from './Modal.svelte';
  import Painike from './Painike.svelte';

  const tapahtumaPeruuta = () => dispatch('peruuta');
  const tapahtumaTallenna = () => dispatch('uusielain', uusiLemmikki);

  let uusiLemmikki = {
    nimi: '',
    kuvaus: '',
    omistaja: '',
  };
  const onkoValidiTekstikentta = (teksti) => teksti.trim().length > 0;
  $: validiNimi = onkoValidiTekstikentta(uusiLemmikki.nimi);
  $: validiKuvaus = onkoValidiTekstikentta(uusiLemmikki.kuvaus);
  $: validiOmistaja = onkoValidiTekstikentta(uusiLemmikki.omistaja);

  let virheviesti = 'Kaikki kentät ovat pakollisia!';
</script>

<Modal>
  <div slot="header">
    <h1>Uusi lemmikki</h1>
  </div>
  <div>
    Nimi: <input
      type="text"
      bind:value={uusiLemmikki.nimi}
      class:tyhja={!validiNimi}
    />
    Kuvaus:
    <input
      type="text"
      bind:value={uusiLemmikki.kuvaus}
      class:tyhja={!validiKuvaus}
    />
    Omistaja:
    <input
      type="text"
      bind:value={uusiLemmikki.omistaja}
      class:tyhja={!validiOmistaja}
    />
  </div>
  {#if !validiNimi || !validiKuvaus || !validiOmistaja}
    <p class="virhe">{virheviesti}</p>
  {/if}
  <div slot="footer">
    <button
      class:tyhja={!validiNimi || !validiKuvaus || !validiOmistaja}
      disabled={!validiNimi || !validiKuvaus || !validiOmistaja}
      on:click={tapahtumaTallenna}>Tallenna</button
    >
    <Painike on:click={tapahtumaPeruuta}>Peruuta</Painike>
  </div>
</Modal>

<style>
  .virhe {
    color: red;
    margin: 0.5rem 0;
  }

  .tyhja {
    border: 2px solid red;
  }
</style>
