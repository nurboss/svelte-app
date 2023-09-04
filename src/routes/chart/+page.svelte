<script>
  import { writable } from 'svelte/store';
  import { onMount } from 'svelte';
  import Chart from 'chart.js/auto'
  import Loading from './loading.svelte';
  const countryDataStore = writable([]);
  let chart;


// Function to fetch data from the API
async function fetchData() {
  try {
    const response = await fetch('https://restcountries.com/v3.1/all');
    console.log(response);
    if (!response.ok) {
      throw new Error('Failed to fetch data');
    }
    const data = await response.json();
    countryDataStore.set(data);
    data.sort((a, b) => b.population - a.population);
    const top10Countries = data.slice(0, 10);
    const labels = top10Countries.map((country) => country.name.common);
    const populations = top10Countries.map((country) => country.population);

    const ctx = document.getElementById('polarAreaChart').getContext('2d');

    chart = new Chart(ctx, {
      type: 'polarArea',
      data: {
        labels: labels,
        datasets: [
          {
            data: populations,
            backgroundColor: [
              'rgba(255, 99, 132, 0.6)',
              'rgba(54, 162, 235, 0.6)',
              'rgba(255, 206, 86, 0.6)',
              'rgba(75, 192, 192, 0.6)',
              'rgba(153, 102, 255, 0.6)',
              'rgba(255, 159, 64, 0.6)',
              'rgba(255, 99, 132, 0.6)',
              'rgba(54, 162, 235, 0.6)',
              'rgba(255, 206, 86, 0.6)',
              'rgba(75, 192, 192, 0.6)',
            ],
            borderWidth: 1,
            borderColor: "#9ca3af",
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        title: {
          display: true,
          text: 'Top 10 Most Populated Countries',
        },
      },
    });

  } catch (error) {
    console.error('Error fetching data:', error);
  }
}

onMount(() => {
  fetchData(); // Fetch data when the component is mounted
});

// Access data from the store
let countries;
countryDataStore.subscribe((value) => {
  countries = value;
});

const getObjectKeys = (data) => {
  if (data && typeof data === "object") {
    const obj = Object.keys(data)[0];
    return obj;
  } else {
    return null;
  }
};

const getObjectValue = (data) => {
  if (data && typeof data === "object") {
    const obj = Object.values(data)[0];
    return obj;
  } else {
    return null;
  }
};

</script>


<svelte:head>
<title>Chart</title>
<meta name="description" content="About this Chart" />
 
</svelte:head>

<div class="flex flex-col-reverse lg:flex-row gap-4  bg-blue-200/50 px-5 sm:px-10 md:px-24 py-5 sm:px:10 md:py-20">

<div class="text-column ">
  {#if countries.length > 0}
  <div class="overflow-x-auto rounded-md">
      <table class="min-w-full bg-white border  border-gray-200 rounded-md">
        <thead>
          <tr class="text-sm ">
             
              <th class="p-5 text-gray-700 font-sans">
                Flag
              </th>
              <th class="p-5 text-gray-700 text-start font-sans">
                Name
              </th>
              <th class="p-5 text-gray-700 text-start font-sans">
                Population
              </th>
              <th class="p-5 text-gray-700 text-start font-sans">
                CIOC
              </th>
              <th class="p-5 text-gray-700 text-start font-sans">
                UN Member Status
              </th>
              <th class="p-5 text-gray-700 text-start font-sans">
                  Currencies(Key)
              </th>
              <th class="p-5 text-gray-700 text-start font-sans">
                Languages
              </th>
            </tr>
        </thead>
        <tbody>
          {#each countries.slice(0,10) as country , i}
          <tr key={i} class="border-t border-gray-200">
      
              <td class="p-5 ">
                <img
                  src={country.flags.png}
                  alt={`Flag of ${country.name.common}`}
                  class="w-8 h-4"
                />
              </td>
              <td class="p-4 font-medium text-gray-500 font-sans">{country.name.common.slice(0,15)}</td>
              <td class="p-4 font-medium text-gray-500 font-sans">{country.population}</td>
              <td class="p-4 font-medium text-gray-500 font-sans text-center">{country.cioc || "-"}</td>
              <td class="p-4 text-center font-medium text-gray-500 font-sans">
                  {#if country.unMember}
                  <span class="font-bold bg-gray-400 rounded-md text-white text-sm px-3 py-1">
                      Yes
                    </span>
                    {:else}
                    <span class="font-bold bg-gray-700 rounded-md text-white text-sm px-3 py-1">
                      No
                    </span>
                  {/if}
                
              </td>
              <td class="p-4 text-center font-medium text-gray-500 font-sans">
                {getObjectKeys(country.currencies)}
              </td>
              <td class="p-4 font-medium text-gray-500 font-sans">
                {getObjectValue(country.languages)}
              </td>
            </tr>
            {/each}
        </tbody>
      </table>
    </div>
  {:else}
    <Loading />
  {/if}
</div>


<div class="border border-gray-200 h-fit bg-white rounded-md flex-1">
<h1 class="px-4 py-2 border-b border-gray-200 font-bold text-gray-700">Countries</h1>
<div class="py-10"><canvas id="polarAreaChart"></canvas></div>
</div>

<style>
canvas {
  max-width: 450px;
  max-height: 400px;
  margin: 0 auto;
}
</style>

</div>
