<script>
  let currentStage = 0;
  const schedule = [
    { time: "6:00 AM", text: "Amina wakes up to her alarm and makes breakfast.", alt: "Amina's bed", img: "images/2.png" },
    { time: "7:00 AM", text: "Catches the bus to her first client's home.", alt: "Amina on the bus", img: "images/3.png" },
    { time: "7:30 AM", text: "Arrives at elderly client's home. Helps with medication, bathing, and breakfast..", alt: "Medication for Amina's client", img: "images/4.png" },
    { time: "9:30 AM", text: "Heads to second client — a woman with early-stage dementia..", alt: "Amina helping her client", img: "images/5.png" },
    { time: "10:00 AM", text: "Assists with meal prep, grocery list, companionship. Writes notes for family caretaker.", alt: "Amina leaving a note", img: "images/6.png" },
    { time: "11:00 AM", text: "Quick lunch: sandwich from home while waiting at the bus stop. Her chest feels tight.", alt: "Amina's sandwhich", img: "images/7.png" },
    { time: "1:00 PM", text: "Final client for the day — recovering post-surgery patient. Administers meds and checks vitals.", alt: "Amina's patient's IV bag", img: "images/8.png"},
    { time: "4:00 PM", text: "Logs reports on paper. Finishes the days visits.", alt: "Pile of reports", img: "images/9.png"},
    { time: "5:00 PM", text: "Heads to her second job - housekeeping at a hotel.", alt: "Amina with her janitor trolley", img: "images/10.png"},
    { time: "10:00 PM", text: "Heads home. Tension headache starting.", alt: "Amina on the bus", img: "images/11.png"},
    { time: "11:00 PM", text: "Arrives home. Quick dinner — reheated rice.", alt: "Amina's microwave", img: "images/12.png"},
    { time: "11:30 PM", text: "Folds laundry. Cleans inhaler, wipes counters.", alt: "Amina's inhaler", img: "images/13.png"},
    { time: "12:00 AM", text: "In bed.", alt: "The moon", img: "images/14.png"},
  ];

  function handleScroll(e) {
    const index = Math.floor(e.target.scrollTop / 200);
    currentStage = Math.min(schedule.length - 1, index);
  }

  export let stage = 0;
  export let altText = '';

  const sceneImages = [
    "/images/2.png",
    "/images/3.png",
    "/images/4.png",
    "/images/5.png",
    "/images/6.png",
    "/images/7.png",
    "/images/8.png",
    "/images/9.png",
    "/images/10.png",
    "/images/11.png",
    "/images/12.png",
    "/images/13.png",
    "/images/14.png",
  ];
</script>

<section class="schedule-intro">
  <h2>Here's what a usual day for her looks like…</h2>
</section>

<div class="scene-container">
  <img src={sceneImages[stage]} alt={altText} />
</div>

<div class="schedule-container">
  <div class="scroll-column" on:scroll={handleScroll}>
    {#each schedule as item}
      <div class="event">
        <h4>{item.time}</h4>
        <p>{item.text}</p>
      </div>
    {/each}
  </div>
  
  <div class="visual-column">
    <img
        src={sceneImages[currentStage]}
        alt={schedule[currentStage].alt}
        class="active"
    />
</div>
</div>

<style>
.schedule-intro {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
  text-align: center;
  padding: 2rem;
  font-family: Optima, sans-serif;
}

.schedule-container {
  display: flex;
  height: 100vh;
  overflow: hidden;
  border: none;
}
.scroll-column {
  width: 50%;
  overflow-y: scroll;
  padding: 2rem;
  box-shadow: none;
  border-right: none;
}
.event {
  height: 200px;
  padding: 1rem;
  border-bottom: 1px solid transparent;
}
.visual-column {
  width: 50%;
  position: sticky;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
img {
  display: none;
  max-height: 60vh;
}
img.active {
  display: block;
  transition: opacity 0.5s ease;
}
</style>
