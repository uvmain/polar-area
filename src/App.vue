<script setup>
import Chart from './components/Chart.vue'
import DownloadButton from './components/DownloadButton.vue'
import { ref } from 'vue'

const inputs = ref([
  { label: "Sales", value: "1" },
  { label: "Traffic", value: "3" },
  { label: "Skills", value: "4" },
  { label: "Energy", value: "2" },
  { label: "Efficiency", value: "5" },
  { label: "Testing", value: "3" }
])

const labels = ref()

</script>

<template>
  <div class="chart-container">
    <div class="input-container">
      <div v-for="(input, index) in inputs" :key="index" class="input-pair">
        <input :id="'label' + index" v-model="input.label" type="text" class="input-item">
        <input :id="'value' + index" v-model="input.value" type="text" class="input-item">
      </div>
    </div>
    <div id="capture-div" class="chart">
      <Chart :inputs="inputs"/>
    </div>
    <DownloadButton />
  </div>
</template>

<style scoped>
.chart-container {
  display: flexbox;
  justify-content: flex-start;
  align-items: flex-center;
  height: 100vh;
  background-color:lightgray;
}
.input-container {
  padding: 20px;
}

.input-pair {
  display: flex;
  margin-bottom: 10px;
}

.input-item {
  color: black;
  margin-right: 10px;
  border: 2px solid #ccc;
  border-radius: 10px;
  font-size: 16px;
  background-color: snow;
  padding: 12px;
}

.chart {
  padding: 10px;
  min-width: 30vw;
}
</style>
