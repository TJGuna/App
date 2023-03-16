<script lang="ts">
  import Chart from 'chart.js/auto';
  import { onMount } from 'svelte';

  let chart;

  onMount(() => {
    const ctx = document.getElementById('myChart').getContext('2d');

    chart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
        datasets: [{
          label: 'Sales',
          data: [12, 19, 3, 5, 2, 3, 14, 6, 11, 8, 4, 7],
          backgroundColor: 'rgba(54, 162, 235, 0.2)',
          borderColor: 'rgba(54, 162, 235, 1)',
          borderWidth: 1
        }]
      },
      options: {
        scales: {
          y: {
            beginAtZero: true
          }
        }
      }
    });
  });
</script>
<div class="w-full">
    <canvas id="myChart"></canvas>
</div>
 