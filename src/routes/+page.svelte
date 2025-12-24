<script>
  let buyPrice = 0;        // average awal
  let lotNumber = 0;       // lot awal
  let targetAverage = 0;   // target new avg
  let newBuyPrice = 0;     // harga beli baru

  let result = 0;
  let newAmount = 0;

  function calculateAdditionalLots() {
    // initial validation
    if (
      buyPrice <= 0 ||
      lotNumber <= 0 ||
      targetAverage <= 0 ||
      newBuyPrice <= 0
    ) {
      result = 0;
      return;
    }

    // logic validation for average down
    if (!(newBuyPrice < targetAverage && targetAverage < buyPrice)) {
      result = 0;
      newAmount = 0;
      return;
    }

    const raw =
      (lotNumber * (buyPrice - targetAverage)) /
      (targetAverage - newBuyPrice);

    if (raw <= 0 || !isFinite(raw)) {
      result = 0;
      newAmount = 0;
      return;
    }
    result = Math.ceil(raw);
    newAmount = result * newBuyPrice * 100;

  }
</script>

<div class="container">
  <h1><u><i>Calc</i></u></h1>

  <p>Harga beli rata-rata</p>
  <input bind:value={buyPrice} type="number" />

  <p>Jumlah lot</p>
  <input bind:value={lotNumber} type="number" />

  <p>Target average baru</p>
  <input bind:value={targetAverage} type="number" />

  <p>Harga beli baru</p>
  <input bind:value={newBuyPrice} type="number" />

  <button on:click={calculateAdditionalLots}>Hitung</button>

  {#if result > 0}
    <p>
      Kamu perlu beli tambahan sebanyak <b>{result}</b> lot,
      senilai <b>Rp {newAmount.toLocaleString("id-ID")}</b>
    </p>
  {/if}
</div>


<style>
  .container {
    padding: 0 100px;
  }
</style>
