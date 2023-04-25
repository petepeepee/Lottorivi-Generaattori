<script>
  import Button from './Button.svelte';
  //koodi omaa
  const minLuku = 1;
  const maxLuku = 40;

  let naytaRivi = false;

  let lottoRivi = [];
  const numero = () => {
    lottoRivi = [];
    naytaRivi = !naytaRivi;
    for (let i = 0; lottoRivi.length < 8; i++) {
      let n = Math.floor(Math.random() * (maxLuku - minLuku) + minLuku);
      if (lottoRivi.includes(n)) {
        n = Math.floor(Math.random() * (maxLuku - minLuku) + minLuku);
      } else {
        lottoRivi.push(n);
      }
    }
    lottoRivi.sort(function (a, b) {
      return a - b;
    });
    console.log(lottoRivi);
  };
</script>

<main>
  <div class="generaattori">
    <div class="yläosa">
      {#if !naytaRivi}
        <h2>Nappia painamalla arvot lottonumerot sekä lisänumeron!</h2>
      {:else}
        <h2>Tadaa!</h2>
      {/if}
      <Button text="Arvo" on:click={numero} />
      <br />
    </div>
    <div class="numerot">
      {#if naytaRivi}
        {#each lottoRivi as numero}
          <h2>{numero}</h2>
        {/each}
      {/if}
    </div>
  </div>
</main>

<style>
  .generaattori {
    padding: 1em;
    border-radius: 20px;
    width: 600px;
    margin: 5em;

    border: 2px solid #eadb08;
    -webkit-box-shadow: -10px 0px 13px -7px #000000, 10px 0px 13px -7px #000000,
      5px 5px 15px 5px rgba(0, 0, 0, 0);
    box-shadow: -10px 0px 13px -7px #000000, 10px 0px 13px -7px #000000,
      5px 5px 15px 5px rgba(0, 0, 0, 0);
  }

  .numerot {
    margin: auto;
    display: flex;
    float: left 10px;
  }

  .numerot h2 {
    width: 35px;
    margin: auto;
    background-color: yellow;
    border-radius: 50%;
  }
</style>
