<script lang="ts">
    import Chart from 'chart.js/auto';
    import type { ScriptableContext } from 'chart.js';
     import { onMount } from 'svelte';

  let chart;

  const data = {
    labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
    datasets: [{
      label: 'Sales',
      fill: true,
      data: [12, 19, 3, 5, 2, 3, 14, 6, 11, 8, 4, 7],
      backgroundColor: (ctx: ScriptableContext<"line">) => {
        const gradient = ctx.chart.ctx.createLinearGradient(0, 0, 0, 450);
        gradient.addColorStop(0, 'rgba(152,222,217,0.9)');
        gradient.addColorStop(0.5, 'rgba(152,222,217,0.5)');
        gradient.addColorStop(1, 'rgba(152,222,217,0.0)');
        return gradient;
      },
      borderColor: "rgba(152,222,217,1)",
    }]
  };

  onMount(() => {
    const ctx = document.getElementById('mylineChart').getContext('2d');
    chart = new Chart(ctx, {
      type: 'line',
      data: data,
      options: {}
    });
  });
  </script>
  <div class="w-full">
      <canvas id="mylineChart"></canvas>
  </div>
   