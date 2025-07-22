<script>
  const whiteIncome = 70000;
  const blackIncome = 44205;
  const gap = whiteIncome - blackIncome;

  const whiteBarWidth = 100; // as percent
  const blackBarWidth = (blackIncome / whiteIncome) * 100;
</script>

<section class="income-gap-container">
  <h3>Texas Median Household Income</h3>

  <div class="bar-row">
    <div class="label">White</div>
    <div class="bar white" style="width: {whiteBarWidth}%">
      <span class="amount">${whiteIncome.toLocaleString()}</span>
    </div>
  </div>

  <div class="bar-row">
    <div class="label">Black</div>
    <div class="bar black" style="width: {blackBarWidth}%">
      <span class="amount">${blackIncome.toLocaleString()}</span>
    </div>
  </div>

  <p class="caption">
    Black households in Texas earn <strong>${gap.toLocaleString()}</strong> less on average than White households. Black residents make up just <strong>9.2%</strong> of the population.
  </p>
</section>

<style>
  .income-gap-container {
    padding: 2rem;
    font-family: Optima, sans-serif;
    max-width: 800px;
    margin: 0 auto;
  }

  h3 {
    text-align: center;
    margin-bottom: 2rem;
  }

  .bar-row {
    display: flex;
    align-items: center;
    margin: 1rem 0;
  }

  .label {
    width: 60px;
    font-weight: bold;
  }

  .bar {
    height: 30px;
    position: relative;
    border-radius: 5px;
    margin-left: 1rem;
  }

  .bar.white {
    background: #9020fe;
  }

  .bar.black {
    background: #53029d;
  }

  .amount {
    position: absolute;
    right: 10px;
    top: 4px;
    font-size: 0.85rem;
    color: #ececec;
  }

  .caption {
    margin-top: 2rem;
    font-size: 1rem;
    text-align: center;
    color: #333;
  }
</style>
