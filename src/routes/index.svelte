<script>
  import LabeledInput from '../components/LabeledInput.svelte';
  import Numpad from '../components/Numpad.svelte';
  import Centered from '../components/Centered.svelte';


  let step = 0;
  let num = 1;
  let firstFlat = 1;
  let flats = 4;
  let newNumber = false;

  $: floor = Math.ceil((num - firstFlat + 1) / flats) - 1;

  const handleClick = (key) => () => {
    switch (key) {
      case '<': {
        if (step > 0) {
          step -= 1;
          newNumber = true;
        }
        break;
      }
      case '>': {
        if (step < 2) {
          step += 1;
          newNumber = true;
        }
        break;
      }
      default: {
        switch (step) {
          case 0:
            {
              if (newNumber) {
                num = key;
                newNumber = false;
              } else {
                num = +(num.toString() + key.toString());
              }
            }
            break;
          case 1:
            if (newNumber) {
              firstFlat = key;
              newNumber = false;
            } else {
              firstFlat = +(firstFlat.toString() + key.toString());
            }
            break;
          case 2:
            if (newNumber) {
              flats = key;
              newNumber = false;
            } else {
              flats = +(flats.toString() + key.toString());
            }
            break;
        }
      }
    }
  };
</script>

<!-- ----------------------------------------------------- -->
<small class="header"
  ><span>Delivery guy helper - Calculate floor of the flat you are looking for</span><span
    >by <a href="http://kjaku.github.io/" noopener noreferrer target="_blank"
      >kjaku</a
    ></span
  ></small
>
<Centered width={600}>
  <h1 style="text-align: center">"Which floor?"</h1>
  <div class="info">
    <LabeledInput thisStep={0} {step} label="flat nr" value={num} />
    <LabeledInput thisStep={1} {step} label="first flat nr" value={firstFlat} />
    <LabeledInput
      thisStep={2}
      {step}
      label="flats on floor"
      value={flats}
      min={2}
    />
    <div style="margin-left: auto" class="result">FLOOR</div>
    <div class="result">
      {floor}
    </div>
  </div>
  <Numpad {handleClick} />
</Centered>

<!-- ----------------------------------------------------- -->
<style>
  a {
    color: inherit;
    text-decoration: underline;
  }
  .info {
    display: grid;
    grid-template-columns: 1fr 1fr;
    justify-items: center;
    align-items: center;
  }
  .result {
    font-size: 2.5rem;
    font-weight: 800;
    padding: 16px;
  }
  .header {
    display: flex;
    opacity: 0.6;
    justify-content: space-between;
  }
</style>
