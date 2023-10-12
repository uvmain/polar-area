<script setup>
import Chart from './components/Chart.vue'
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
        <div class="input-item">
          <input :id="'label' + index" v-model="input.label" type="text">
        </div>
        <div class="input-item">
          <input :id="'value' + index" v-model="input.value" type="text">
        </div>
      </div>
    </div>
    <div class="chart">
      <Chart :inputs="inputs"/>
    </div>
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
  flex: 2;
  align-items: flex-center;
  margin-right: 10px;
  color: black;
}

.input-item input {
  color: black;
  background-color: white;
}

.chart {
  padding: 10px;
  min-width: 30vw;
}
</style>
