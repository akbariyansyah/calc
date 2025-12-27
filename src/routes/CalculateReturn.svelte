<script lang="ts">
  let buyPrice = 0;
  let lotNumber = 0;
  let sellPrice = 0;

  let percentageValue = 0;
  let profit = 0;

  function calculateReturns() {
    const shares = lotNumber * 100;
    const modal = buyPrice * shares;
    const sellValue = sellPrice * shares;
    profit = sellValue - modal;
    percentageValue = modal === 0 ? 0 : Math.ceil((profit / modal) * 100);
  }
</script>

<div class="container">
  <h3>Hitung potensial return</h3>
  <p>Harga beli rata-rata</p>
  <input bind:value={buyPrice} type="number" />

  <p>Jumlah lot</p>
  <input bind:value={lotNumber} type="number" />

  <p>Target harga jual</p>
  <input bind:value={sellPrice} type="number" />

  <button onclick={calculateReturns}>Hitung</button>

  {#if percentageValue > 0}
    <p>Profit kamu sebesar {percentageValue} %, senilai Rp {profit.toLocaleString("id-ID")}</p>
    {:else if percentageValue < 0}
    <p>Kamu rugi sebesar {percentageValue} %, senilai Rp {profit.toLocaleString("id-ID")}</p>
  {/if}
</div>


