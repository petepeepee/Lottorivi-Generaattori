<script>
  //koodi otettu kurssilla tehdystä buttonista ja muokattu
  export let disabled = false;
  export let text = '';
</script>

<button {disabled} on:click>{text}<slot /></button>

<style>
  button {
    margin: auto;
    color: rgb(249, 250, 249);
    background-color: rgb(111, 8, 59);
    font: bold;
    font-size: 2em;
    border-radius: 5%;
  }

  button:disabled,
  button[disabled] {
    border: 1px solid #999999;
    background-color: #cccccc69;
    color: #666666;
  }
</style>
