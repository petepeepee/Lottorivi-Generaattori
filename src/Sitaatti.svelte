<script>
  //onMountiin on katsottu mallia kurssimateriaalista
  import { onMount } from 'svelte';
  let sitaatti = '';

  onMount(async () => {
    const response = await fetch(`https://api.kanye.rest/`);
    if (!response.ok) {
      throw new Error('cannot fetch the data');
    }
    sitaatti = await response.json();
  });
</script>

<main>
  <div class="sitaatti">
    <img src="./pics/R.png" alt="kanye" width="100px" />
    <!--<a href=https://www.pngall.com/kanye-west-png/download/9724 target="_blank">Kanye West PNG Pic</a> Kuva täältä, kuvaajaa ei erikseen mainita.-->
    <h2>{sitaatti.quote}</h2>
  </div>
</main>

<style>
  .sitaatti {
    padding: 1em;
    margin: 0;
    border-radius: 20px;
    width: 600px;
    margin: 5em;

    border: 2px solid #eadb08;
    -webkit-box-shadow: -10px 0px 13px -7px #000000, 10px 0px 13px -7px #000000,
      5px 5px 15px 5px rgba(0, 0, 0, 0);
    box-shadow: -10px 0px 13px -7px #000000, 10px 0px 13px -7px #000000,
      5px 5px 15px 5px rgba(0, 0, 0, 0);
  }
</style>
