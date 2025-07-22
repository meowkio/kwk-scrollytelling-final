<script>
  import { fade } from 'svelte/transition';
  import { typewriter } from './transition.js' // typewriter effect I got from Svelte Key blocks tutorial
	import { messages } from './typewriter-messages.js';

  import AminaIDCard from './lib/AminaID.svelte';
	let i = $state(-1);

  $effect(() => {
    // interval only runs until last message
    if (i < messages.length - 1) {
      const interval = setInterval(() => {
        i += 1;
        if (i >= messages.length - 1) {
          clearInterval(interval); // stop after last message
        }
      }, 2500);

		return () => {
			clearInterval(interval);
    }
  }});

  import DailySchedule from './lib/DailySchedule.svelte';

  import IncomeGap from './lib/IncomeGap.svelte';
  
  import HospitalBill from "./lib/HospitalBill.svelte";
  import billData from "./data/hospital-bill.json";

  const bills = /** @type {any[]} */ (billData); //billData was being treated as unknown and not an array.. so this helped!

  import InsuranceCoverage from './lib/InsuranceCoverage.svelte';
  
  import DragDrop from './lib/DragDrop.svelte';

  import FinalMessage from './lib/FinalMessage.svelte';

</script>

<h1 in:fade={{ duration: 1500 }} class="main-title">Billed for Breathing</h1>

<div class="typewriter-container">
{#key i}
	<h2 in:typewriter={{ speed: 5 }}>
		{messages[i] || ''}
  </h2>
{/key}
</div>

<AminaIDCard />

<h2>She has Chronic Asthma</h2>

<DailySchedule />

<IncomeGap />

<section class="narrative-section">
  <div class="narrative-text">
    <h2>Amina had her routine check-up today.</h2>
    <p>
      Her chest had felt tight lately, and she finally decided to get it checked out. The clinic wasn’t close, and she had to take time off between jobs—but her breathing was getting worse.
    </p>
    <p>
      She saw a doctor, had a lung test, and got some basic blood work done. It was over in an hour.
    </p>
    <p>
      But now she’s thinking about the cost. She doesn’t have full insurance, and some parts of the visit weren’t covered. Even though she feels a little better, she’s nervous to open the bill.
    </p>
    <p class="narrative-tagline">
      That’s the reality for many like Amina. The fear of a bill can feel heavier than the illness itself.
    </p>
  </div>
</section>


<main>
  <section class="bill-container">
    <h3>{bills[0].title}</h3>
    <HospitalBill billItems={bills[0].items} />
    <p><strong>Total Billed:</strong> ${bills[0].total}</p>
    <p><strong>Amina Pays:</strong> ${bills[0]["total out of pocket"]}</p>
  </section>

  <section class="narrative-section">
  <div class="narrative-text">
    <p>
      Amina stares at the bill after her shift.
    </p>
    <p>
      $310. That’s groceries for four weeks.
    </p>
    <p>
      She thinks about skipping her inhaler refill this month — just for now.
    </p>
    <p>
      This isn't an emergency. Not yet.
    </p>
    <p class="narrative-tagline">
      But when a routine check-up costs nearly half of your weekly pay, it feels like one.
    </p>
  </div>
</section>

<section class="narrative-section">
  <div class="narrative-text">
    <h2>Two weeks later, her breathing gets worse.</h2>
    <p>
      Amina’s been using her inhaler more often.  
      At night, she wakes up gasping. During the day, she wheezes between clients.
    </p>
    <p>
      She doesn’t want to go back — she’s still paying off the last visit.  
      But one afternoon, her chest gets so tight she can’t ignore it anymore.
    </p>
    <p>
      She goes to urgent care, hoping they’ll help.  
      Hoping it won’t cost as much.
    </p>
  </div>
</section>

<DragDrop />

  <section class="bill-container">
    <h3>{bills[1].title}</h3>
    <HospitalBill billItems={bills[1].items} />
    <p><strong>Total Billed:</strong> ${bills[1].total}</p>
    <p><strong>Amina Pays:</strong> ${bills[1]["total out of pocket"]}</p>
  </section>

<section class="narrative-section">
  <div class="narrative-text">
    <h2>She pays what she can.</h2>
    <p>
      The antibiotics helped. The steroids helped.  
      But the bill still hurts more.
    </p>
    <p>
      Amina skips rent for a week.  
      Buys less food.  
      Walks to work instead of taking the bus.
    </p>
    <p class="narrative-tagline">
      Health isn’t the only thing slipping away — so is stability.
    </p>
  </div>
</section>

  <section class="bill-container">
    <h3>{bills[2].title}</h3>
    <HospitalBill billItems={bills[2].items} />
    <p><strong>Total Billed:</strong> ${bills[2].total}</p>
    <p><strong>Amina Pays:</strong> ${bills[2]["total out of pocket"]}</p>
  </section>

  <InsuranceCoverage />

  <FinalMessage />

</main>



<style>

    .main-title {
    text-align: center;
    font-size: 4rem;
    margin-top: 15vh;
    font-weight: 700;
    color: #2c2c2c;
    font-family: Optima, sans-serif;
  }

  .typewriter-container {
    top: 0;
    height: 100vh;
    width: 150vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    background: #b0e0e6;
    z-index: 1;
    font-size: 2rem;
    white-space: nowrap;
    overflow: hidden;
    font-family: Optima, sans-serif;
  }

  DailySchedule {
    margin: 4rem 0;
  }

  h2 {
    margin-bottom: 0.5rem;
    color: #333;
    font-family: Optima, sans-serif;
  }

  h3 {
    font-size: 1.6rem;
    margin-bottom: 0.5rem;
    font-family: "Courier New", Courier, monospace;
    align: center;
  }

  main {
    padding: 2rem;
    font-family: "Courier New", Courier, monospace;
    background-color: #b0e0e6;
    align-items: center;
    display: flex;
    flex-direction: column;
  }

    .bill-container {
  max-width: 320px;
  width: 100%;
  margin: 2rem 0;
  padding: 1.5rem;
  border: 1px solid #ddd;
  background: #f9f9f9;
  text-align: left;
  }

  .narrative-section {
  padding: 4rem 2rem;
  font-family: Optima, sans-serif;
}

.narrative-text {
  max-width: 1000px;
  margin: 0 auto;
  line-height: 1.6;
  font-size: 1.15rem;
}

.narrative-text h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  font-family: Optima, sans-serif;
  color: #000000;
}

.narrative-tagline {
  font-weight: bold;
  font-style: italic;
  margin-top: 2rem;
  font-size: 1.2rem;
}

</style>
