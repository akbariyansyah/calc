<script lang="ts">
  let buyPrice = 0; // average awal
  let lotNumber = 0; // lot awal
  let newBuyPrice = 0; // target new avg
  let newLotNumber = 0; // harga beli baru

  let newAveragePrice = 0;

  function calculateNewAverage() {
    newAveragePrice =
     (( buyPrice * lotNumber ) +
      (newBuyPrice * newLotNumber)) / (lotNumber + newLotNumber);
  }
</script>

<div class="container">
  <h3>Hitung harga rata-rata baru</h3>
  <p>Harga beli rata-rata</p>
  <input bind:value={buyPrice} type="number" />

  <p>Jumlah lot</p>
  <input bind:value={lotNumber} type="number" />

  <p>Harga beli rata-rata baru</p>
  <input bind:value={newBuyPrice} type="number" />

  <p>Jumlah Lot baru</p>
  <input bind:value={newLotNumber} type="number" />

  <button on:click={calculateNewAverage}>Hitung</button>

  {#if newAveragePrice > 0}
    <p>Harga average kamu jadi {newAveragePrice}</p>
  {/if}
</div>

<style>
  .container {
    padding: 0 100px;
    margin-top: 40px;
  }
</style>
