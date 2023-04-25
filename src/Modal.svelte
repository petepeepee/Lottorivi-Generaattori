<script>
  import Button from './Button.svelte';

  export let suljeTeksti = 'Sulje';
  //modal ikkuna otettu kurssin tehtävääni käyttämästä modaali-ikkunasta
</script>

<div class="backdrop" />

<div class="modal">
  <header>
    <slot name="header" />
  </header>
  <slot />
  <footer>
    <slot name="footer">
      <Button on:click>{suljeTeksti}</Button>
    </slot>
  </footer>
</div>

<style>
  .backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.75);
    z-index: 10;
  }

  .modal {
    padding: 1rem;
    position: fixed;
    top: 10vh;
    left: 10vw;
    width: 80%;
    max-height: 80vh;
    background: rgb(219, 150, 23);
    border-radius: 5px;
    z-index: 100;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    overflow: scroll;
  }
</style>
