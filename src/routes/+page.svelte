<script>
  let buyPrice = 0;
  let lotNumber = 0;
  let targetPrice = 0;
  let newAveragePrice = 0;

  let result = 0;

  function calculateAdditionalLots() {
    if (newAveragePrice === targetPrice) {
      result = 0;
      return;
    } else {
        result = (lotNumber * (buyPrice - newAveragePrice)) / (newAveragePrice - targetPrice);
    }
  }
</script>

<div class="container">
  <h1><u><i>Calc</i></u></h1>
  <h2>Hitung Nilai saham untuk average down/up</h2>
  <p>Harga beli saham</p>
  <input placeholder="Harga Beli" bind:value={buyPrice} type="number" />
  <p>Jumlah lot</p>
  <input placeholder="Jumlah Lot Saham" bind:value={lotNumber} type="number" />
  <p>
    tipe
  </p>
  <select>
    <option value="down">Average Down</option>
    <option value="up">Average Up</option>
  </select>
  <p>Harga target</p>
  <input placeholder="harga target" bind:value={targetPrice} type="number" />
  <p>Harga beli baru</p>
  <input placeholder="harga  average baru" bind:value={newAveragePrice} type="number" />
  <button onclick={() => calculateAdditionalLots()}>Hitung</button>

    <h3>Hasil: </h3>
    {#if result > 0}
    <p>Kamu perlu beli tambahan sebanyak {result} lot</p>
    {:else} 
    <p></p>
    {/if}
</div>

<style>
    .container {
        padding:0 100px;
    }
</style>