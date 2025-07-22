<script>
  export let scrollEnded = false;
</script>

<section class="final-message" in:fade>
  <h1>This isn’t just a story.</h1>
  <p>Amina’s story is real.</p>
  <p>Medical debt is the #1 cause of personal bankruptcy in the U.S.</p>
  <a href="https://blackwealthdata.org/" target="_blank">See what policies can change this →</a>
</section>

<style>
  .final-message {
    padding: 4rem 2rem;
    color: rgb(52, 52, 52);
    font-family: Optima, sans-serif;
    text-align: center;
  }

  .final-message h1 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }

  .final-message p {
    font-size: 1.3rem;
    margin: 1rem 0;
  }

  .final-message a {
    margin-top: 2rem;
    display: inline-block;
    color: black;
    padding: 0.75rem 1.5rem;
    border-radius: 0.5rem;
    text-decoration: none;
    font-weight: bold;
    transition: 0.3s;
  }

  .final-message a:hover {
    background: #f5a4ba;
  }
</style>
