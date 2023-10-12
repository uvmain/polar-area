<script setup>
import Chart from './components/Chart.vue'
import { ref } from 'vue';

const inputs = ref([
  { label: "Sales", value: "" },
  { label: "Traffic", value: "" },
  { label: "Skills", value: "" },
  { label: "Energy", value: "" },
  { label: "Features", value: "" }
])

</script>

<template>
  <div class="chart-container">
    <div class="input-container">
      <div v-for="(input, index) in inputs" :key="index" class="input-pair">
        <div class="input-item">
          <label :for="'label' + index">Label {{ index + 1 }}</label>
          <input :id="'label' + index" v-model="input.label" type="text">
        </div>
        <div class="input-item">
          <label :for="'value' + index">Value {{ index + 1 }}</label>
          <input :id="'value' + index" v-model="input.value" type="text">
        </div>
      </div>
    </div>
    <div class="chart">
      <!-- Include your chart component here -->
      <Chart />
    </div>
  </div>
</template>

<style scoped>
.chart-container {
  display: flex;
  background-color:lightgray;
}

.input-container {
  flex: 1;
  padding: 20px 50px 20px 20px;
}

.input-pair {
  display: flex;
  margin-bottom: 10px;
}

.input-item {
  flex: 1;
  margin-right: 10px;
  color: black;
}

.input-item input {
  color: black;
  background-color: white;
}

.chart {
  flex: 2;
  padding: 20px;
}
</style>
