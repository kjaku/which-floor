<script>
  export let thisStep;
  export let step;
  export let label;
  export let value;
  export let min ="0";
</script>

<div class="label">{label}</div>
<div class={thisStep === step ? 'currentStep' : 'unselectedStep'}>
  <input bind:value {min} readonly/>
</div>

<style>
  input {
    border: none;
    background-color: transparent;
    border-bottom: 3px solid;
    max-width: 100px;
    text-align: center;
    font-size: 2rem;
    font-weight: 800;
    margin: 16px;
  }
  .label {
    text-transform: uppercase;
    font-size: 1.25rem;
    font-weight: 800;
    margin-left: auto;
  }
  .unselectedStep {
    border: 4px solid transparent;
  }
  .currentStep {
    border: 4px solid darkred;
    border-radius: 12px;
  }
</style>
