<script setup>
import { onMounted } from 'vue'
import Chart from 'chart.js/auto'

async function generateChart() {
  const data = [
    { year: 2010, count: 10 },
    { year: 2011, count: 20 },
    { year: 2012, count: 15 },
    { year: 2013, count: 25 },
    { year: 2014, count: 22 },
    { year: 2015, count: 30 },
    { year: 2016, count: 28 },
  ];

  new Chart(
    document.getElementById('chart'),
    {
      type: 'polarArea',
      data: {
        labels: ['Label 1', 'Label 2', 'Label 3', 'Label 4'],
        datasets: [
          {
            data: [10, 20, 30, 40],
            backgroundColor: ['rgba(255, 99, 132, 0.5)', 'rgba(54, 162, 235, 0.5)', 'rgba(255, 206, 86, 0.5)', 'rgba(75, 192, 192, 0.5)'],
          },
        ],
      },
      options: {
        responsive: true,
        scales: {
          r: {
            pointLabels: {
              display: true,
              centerPointLabels: true,
              font: {
                size: 18
              }
            }
          }
        },
        plugins: {
          legend: {
            display: false
          },
          title: {
            display: false,
            text: 'Chart.js Polar Area Chart With Centered Point Labels'
          }
        }
      },
    }
  )
};

onMounted(() => {
  generateChart()
})
</script>

<template>
  <div>
    <div style="width: 800px;">
      <canvas id="chart" />
    </div>
  </div>
</template>