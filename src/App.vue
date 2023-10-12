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

function addInputPair() {
  inputs.value.push({ label: '', value: '' })
}

function removeInputPair(index) {
  inputs.value.splice(index, 1)
}
</script>

<template>
  <div class="chart-container">
    <div class="input-container">
      <div v-for="(input, index) in inputs" :key="index" class="input-pair">
        <input :id="'label' + index" v-model="input.label" type="text" class="input-item">
        <input :id="'value' + index" v-model="input.value" type="text" class="input-item">
        <button @click="removeInputPair(index)" class="remove-button">Remove</button>
      </div>
      <button @click="addInputPair" class="add-button">Add Dataset</button>
      <DownloadButton class="download-button"/>
    </div>
    <div id="capture-div" class="chart">
      <Chart :inputs="inputs"/>
    </div>
  </div>
</template>

<style scoped>
.chart-container {
  display: inline-flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
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
.download-button {
  margin-top: 40px;
}
.remove-button {
  background-color: #acacac;
  border: none;
  color: white;
  padding: 10px;
  border-radius: 10px;
  cursor: pointer;
  margin: 5px;
  font-size: smaller;
}

.add-button {
  margin-top: 10px;
  background-color: #acacac;
  border: none;
  color: white;
  padding: 10px;
  border-radius: 10px;
  cursor: pointer;
}
</style>
