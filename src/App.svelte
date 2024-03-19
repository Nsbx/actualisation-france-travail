<script>
  import Logo from './assets/France-travail-2023.svg';
  import Const from './utils/const';
  import Counter from './lib/Counter.svelte';
  import RefreshEventButton from './lib/RefreshEventButton.svelte';
  import PaymentEventButton from './lib/PaymentEventButton.svelte';
</script>

<main>
  <div>
    <a href={Const.FRANCE_TRAVAIL_URL} target="_blank" rel="noreferrer">
      <img src={Logo} class="logo" alt="France Travail" />
    </a>
  </div>

  <RefreshEventButton />
  <PaymentEventButton />
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em white);
  }
</style>
