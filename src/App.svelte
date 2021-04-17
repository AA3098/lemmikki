<script>
  import Banner from './Banner.svelte';
  import Hoitovinkki from './Hoitovinkki.svelte';
  import Painike from './Painike.svelte';
  import Lemmikit from './Lemmikit.svelte';
  import UusiElain from './UusiElain.svelte';

  let elain = {
    haku: 'cat',
    laji: 'Kissa',
  };

  let lemmikki = {
    nimi: '',
    kuvaus: '',
    omistaja: '',
  };

  let lemmikit = [
    {
      nimi: 'Pörrö',
      kuvaus: 'Tuttavallinen ja leikkisä',
      omistaja: 'Pekka Pekkanen',
    },
    { nimi: 'JoJo', kuvaus: 'Urhollinen ja Rohkea', omistaja: 'Speedwagon' },
    {
      nimi: 'Mario',
      kuvaus: 'Auttavainen ja Pulska',
      omistaja: 'Prinsessa Persikka',
    },
  ];

  let nakyvyysAika = 3000;

  const lisaaElukka = (ce) => {
    lemmikit.push(ce.detail);
    lemmikit = lemmikit;
  };

  const clear = () => {
    lemmikki.nimi = '';
    lemmikki.kuvaus = '';
    lemmikki.omistaja = '';
  };
  const piilota = () => (piilotaTiedot = !piilotaTiedot);

  let piilotaTiedot = false;

  const peruutaModal = () => {
    piilotaTiedot = false;
  };

  const yeetThis = (ce) => {
    lemmikit = lemmikit.filter((lemmikki) => lemmikki.nimi !== ce.detail);
  };
  const print = () => {
    console.log(lemmikit);
  };
</script>

<main>
  <Banner />
  <Hoitovinkki {nakyvyysAika} />
  <Lemmikit {...elain} {lemmikit} on:poista={yeetThis} />
  {#if piilotaTiedot}
    <UusiElain {elain} on:peruuta={peruutaModal} on:uusielain={lisaaElukka} />
  {/if}
  <Painike on:click={piilota}>Lisää uusi</Painike>
  <button on:click={print}>printtaa</button>
  <br />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
