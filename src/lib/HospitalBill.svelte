<script>
  export let billItems = [];
</script>

<section>
  <h2>Hospital Bill</h2>
  <ul>
    {#each billItems as item}
      <li class={item.covered ? "covered" : "uncovered"}>
        <div class="line">
          {item.description} ---- ${item.amount}
        </div>
        {#if item.covered && item.patientPays}
          <div class="note">
            → {item.note} — ${item.patientPays}
          </div>
        {/if}
      </li>
    {/each}
  </ul>
</section>

<style>
  ul {
    list-style: none;
    padding: 0;
  }

  li {
    font-size: 1.1rem;
    margin: 0.75rem 0;
  }

  .covered {
    color: #aaa;
  }

  .covered .line {
    text-decoration: line-through;
  }

  .uncovered {
    font-weight: bold;
    color: #c0392b;
  }

  .note {
    margin-left: 1.5rem;
    font-size: 0.95rem;
    color: #555;
    font-style: italic;
  }
</style>
