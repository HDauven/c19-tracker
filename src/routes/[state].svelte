<script context="module">
  import stateNames from "../data/stateNames.js";
  import requests from "../data/requests.js";

  export async function preload(page) {
    const state = page.params["state"];
    if (stateNames.find(s => s.abbreviation === state) === undefined) {
      this.error(404, "State not found");
      return;
    }

    const fullStateName = stateNames.find(s => s.abbreviation === state).name;

    try {
      const stats = await requests.stateStats(state);
      const historic = await requests.historicState(state);
      const statesData = await requests.statesData();
      return { state: fullStateName, stats, historic, statesData };
    } catch (error) {
      this.error(
        500,
        "There was an error in calling the api, please try again in 5 minutes."
      );
      return;
    }
  }
</script>

<script>
  import CovidStat from "../components/CovidStat.svelte";
  import CovidChart from "../components/CovidChart.svelte";
  import TableContainer from "../components/TableContainer.svelte";

  export let state;
  export let stats;
  export let historic;
  export let statesData;
</script>

<svelte:head>
  <title>Covid 19 Tracker {state}</title>
</svelte:head>

<div class="section header">
  <div class="container">
    <h1>Covid 19 - {state}</h1>
  </div>
</div>

<CovidStat {...stats} />
<CovidChart historicData={historic} title="COVID-19 - {state}" />

<TableContainer data={statesData} />
