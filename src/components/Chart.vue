<script setup>
import { onMounted, ref, watchEffect } from 'vue'
import Chart from 'chart.js/auto'
import uniqolor from 'uniqolor'

let chartInstance = null

const props = defineProps({
  inputs: {
    type: Array,
    required: true
  }
})

const data = ref([])
const labels = []
const datasets = []
const colours = []

function generateData() {
  labels.length = 0
  datasets.length = 0
  colours.length = 0
  for (const input of props.inputs) {
    labels.push(input.label)
    datasets.push(input.value)
    colours.push(uniqolor(input.label, { format: 'rgb' }).color)
  }
  data.value = {
    labels,
    datasets,
    colours
  }
}

async function generateChart() {
  if (chartInstance) {
    chartInstance.destroy()
  }
  chartInstance = new Chart(
    document.getElementById('chart'),
    {
      type: 'polarArea',
      data: {
        labels: labels,
        datasets: [
          {
            data: datasets,
            backgroundColor: colours,
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
          }
        }
      },
    }
  )
}

onMounted(() => {
  generateData()
  generateChart()
})

watchEffect(() => {
  generateData()
  generateChart()
})
</script>

<template>
  <div>
    <div>
      <canvas id="chart" />
    </div>
  </div>
</template>