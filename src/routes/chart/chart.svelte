<script>
    import { onMount } from 'svelte';
    import Chart from 'chart.js/auto'
  
    let chart;
  
    onMount(async () => {
        const response = await fetch('https://restcountries.com/v3.1/all');
      if (!response.ok) {
        throw new Error('Failed to fetch data');
      }
      const countryData = await response.json();
      countryData.sort((a, b) => b.population - a.population);
      const top10Countries = countryData.slice(0, 10);
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
    });
  </script>
  
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
  