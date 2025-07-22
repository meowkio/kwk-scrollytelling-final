<script>
  export let name = "Amina Thomas";
  export let age = 28;
  export let job = "Home Health Aide";
  export let location = "Houston, Texas";
  export let insurance = "Employer Insurance";
  export let image = "/images/amina-portrait.png";
</script>

<div class="id-card">
  <div class="id-header">
    <div class="state-title">TEXAS ID CARD</div>
    <div class="state-star">★</div>
  </div>

  <div class="id-body">
    <img class="id-photo" src={image} alt="Amina's ID photo" />
    <div class="id-info">
      <p><strong>Name:</strong> {name}</p>
      <p><strong>Age:</strong> {age}</p>
      <p><strong>Occupation:</strong> {job}</p>
      <p><strong>Location:</strong> {location}</p>
      <p><strong>Insurance:</strong> {insurance}</p>
    </div>
  </div>

  <div class="id-footer">
    <div class="signature">
      <span class="label">Signature:</span>
      <span class="name">{name}</span>
    </div>
    <div class="barcode"></div>
  </div>
</div>

<style>
  .id-card {
    width: 460px;
    margin: 10vh auto;
    border-radius: 8px;
    background: #ffffff;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    font-family: 'Courier New', monospace;
    border: 3px solid #1f1f1f;
    overflow: hidden;
    animation: fadeIn 1s ease-in;
    align-content: right;
  }

  .id-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #002868;
    color: white;
    padding: 0.75rem 1rem;
    font-size: 1.2rem;
    font-weight: bold;
  }

  .state-title {
    letter-spacing: 1.5px;
  }

  .state-star {
    font-size: 1.5rem;
    color: #ffcc00;
  }

  .id-body {
    display: flex;
    padding: 1rem;
  }

  .id-photo {
    width: 98px;
    height: 118px;
    object-fit: cover;
    border: 2px solid #000;
    margin-right: 1rem;
    background: #ccc;
  }

  .id-info p {
    margin: 0.4rem 0;
    font-size: 0.95rem;
    color: #333;
  }

  .id-footer {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0.5rem 1rem 1rem 1rem;
  }

  .signature {
    margin-bottom: 1rem;
    font-family: 'Snell Roundhand', cursive;
    font-size: 1.1rem;
    color: #333;
  }

  .signature .label {
    font-family: 'Courier New', monospace;
    font-size: 0.8rem;
    font-weight: normal;
    color: #555;
    margin-right: 0.5rem;
  }

  .barcode {
    width: 100%;
    height: 20px;
    background-image: repeating-linear-gradient(
      to right,
      #000,
      #000 2px,
      #fff 2px,
      #fff 4px
    );
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }
</style>