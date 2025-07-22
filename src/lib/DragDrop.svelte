<script>
  let covered = [];
  let notCovered = [];

  let procedures = [
    "ER Facility Fee",
    "Nebulizer Treatment",
    "Chest X-Ray",
    "Oxygen Administration"
  ];

  function handleMove(item, target) {
    // Prevent duplicates
    if (!covered.includes(item) && !notCovered.includes(item)) {
      if (target === "covered") {
        covered = [...covered, item];
      } else {
        notCovered = [...notCovered, item];
      }
      // Remove from procedures
      procedures = procedures.filter((p) => p !== item);
    }
  }

  $: allPlaced = procedures.length === 0;
</script>

<section class="drag-container">
  <h2>What does her insurance actually cover?</h2>
  <p>Decide where each procedure should go.</p>

  <div class="drag-lists">
    <div class="column">
      <h3>Procedures</h3>
      {#each procedures as proc}
        <div class="item">
          {proc}
          <button on:click={() => handleMove(proc, "covered")}>Covered</button>
          <button on:click={() => handleMove(proc, "not")}>Not Covered</button>
        </div>
      {/each}
    </div>

    <div class="column">
      <h3>Covered</h3>
      {#each covered as proc}
        <div class="item covered">{proc}</div>
      {/each}
    </div>

    <div class="column">
      <h3>Not Covered</h3>
      {#each notCovered as proc}
        <div class="item not-covered">{proc}</div>
      {/each}
    </div>
  </div>

  {#if allPlaced}
    <div class="reality-message">
      <p>Scroll down to see what her reality is actually like.</p>
    </div>
  {/if}
</section>

<style>
  .drag-container {
    padding: 2rem;
    text-align: center;
    font-family: Optima, sans-serif;
    background: #ffffff9a;
  }

  .drag-lists {
    display: flex;
    justify-content: space-around;
    margin-top: 2rem;
    flex-wrap: wrap;
  }

  .column {
    flex: 1;
    min-width: 250px;
    margin: 0 1rem;
  }

  .item {
    background: white;
    padding: 0.5rem;
    margin: 0.5rem 0;
    border: 1px solid #ccc;
    border-radius: 0.3rem;
  }

  .covered {
    background: #d6f5d6;
  }

  .not-covered {
    background: #f9d2d2;
  }

  button {
    margin-left: 0.5rem;
    padding: 0.3rem 0.6rem;
    font-size: 0.9rem;
    border: none;
    border-radius: 0.3rem;
    cursor: pointer;
    background: #ddd;
  }

  .reality-message {
    margin-top: 2rem;
    font-size: 1.3rem;
    color: #444;
    font-weight: bold;
    animation: fadeIn 1s ease forwards;
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }
</style>
