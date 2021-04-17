<script>
  import Tietokortti from './Tietokortti.svelte';
  export let haku;
  export let laji;
  export let lemmikit;
</script>

<div>
  {#each lemmikit as elukka}
    <Tietokortti {haku} {...elukka} {laji} on:poista />
  {/each}
</div>
