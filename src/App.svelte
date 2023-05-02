<script>
  //Vaikkakin luulen, että spagetista voi päätellä niin kaikki on minun koodiani
  // if lohko on sitä varten, että jos käyttäjä painaa kyllä ja haluaa arpoa lottorivin, aukeaa modaali-ikkuna jossa voi tämän arpoa, jos taas ei, sitaatti-button tulee näkyviin, jota painamalla tulee modaali-ikkuna jossa on sitaatti.
  //Kun modaali-ikkunat sulkee nollaafunktio palauttaa sivun lähtötilanteen ja käyttäjä voi tehdä uuden valinnan
  import Button from './Button.svelte';
  import Modal from './Modal.svelte';
  import Title from './Title.svelte';
  import Footer from './Footer.svelte';
  import Generator from './Generator.svelte';
  import Sitaatti from './Sitaatti.svelte';

  let nayta = false;
  const kylla = () => {
    nayta = !nayta;
    elaNayta = true;
    naytaLottorivi = !naytaLottorivi;
    lottoSuljettu = !lottoSuljettu;
  };

  let elaNayta = false;
  const ei = () => {
    elaNayta = !elaNayta;
    nayta = false;
    naytaSitaatti = !naytaSitaatti;
  };

  let suljettu = true;
  const avattu = () => {
    suljettu = !suljettu;
    lottoSuljettu = false;
  };

  let lottoSuljettu = false;

  let naytaSitaatti = false;
  let naytaLottorivi = false;

  const nollaa = () => {
    lottoSuljettu = false;
    suljettu = true;
    elaNayta = false;
    nayta = false;
    naytaSitaatti = false;
    naytaLottorivi = false;
  };
</script>

<main>
  <Title />
  {#if !elaNayta}
    <h2>Haluatko arpoa lottorivin?</h2>
  {:else}
    <h2>Katso satunnainen sitaatti piristämään päivääsi!</h2>
  {/if}

  <Button text="Kyllä" disabled={elaNayta} on:click={kylla} />

  <Button text="Ei" disabled={elaNayta} on:click={ei} />

  {#if lottoSuljettu}
    <Modal on:click={nollaa}><Generator /></Modal>
  {/if}

  <Button text="Sitaatti" disabled={!naytaSitaatti} on:click={avattu} />
  {#if !suljettu}
    <Modal on:click={nollaa}><Sitaatti /></Modal>
  {/if}

  <Footer />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 600px;
    height: 100%;
    margin: 0 auto;
    background-color: rgb(219, 150, 23);
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
