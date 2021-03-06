<script>
  export let cases;
  export let deaths;
  export let recovered;
  export let ventilator;
  export let hospitalized;
  export let icu;
  export let tested;
  export let updated;
</script>

<style>
  .columns {
    border: solid 1px black;
  }
</style>

<div class="section">
  <div class="container">
    <div class="columns">
      <h3 class="is-3 column">Cases: {cases}</h3>
      <h3 class="is-3 column">Deaths: {deaths}</h3>
      <h3 class="is-3 column">Recovered: {recovered}</h3>
      <h3 class="is-3 column">Updated: {updated}</h3>
    </div>
  </div>
</div>
<div class="section">
  <div class="container">
    <div class="columns">
      <h3 class="is-3 column">Tested: {tested}</h3>
      <h3 class="is-3 column">Hospitalized: {hospitalized}</h3>
      <h3 class="is-3 column">Total ICU: {icu}</h3>
      <h3 class="is-3 column">Total Ventilator: {ventilator}</h3>
    </div>
  </div>
</div>
