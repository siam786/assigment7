<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue";

let chart = null;
const newNumber = ref(0);
const dataset = [25, 16, 7, 3, 14];

const data = {
  labels: ["Amaranth", "Blue", "Yellow","Silver"],
  datasets: [
    {
      label: "My Dataset",
      data: [450, 150, 100,150],
      backgroundColor: [
        "	rgb(159, 43, 104)",
        "rgb(54, 162, 235)",
        "rgb(255, 205, 86)",
        "rgb(192,192,192)",
      ],
      hoverOffset: 4,
    },
  ],
};
// </block:setup>

// <block:config:0>
const config = {
  type: "pie",
  data: data,
};

onMounted(() => {
  const ctx = document.getElementById("myChart");
  chart = new Chart(ctx, config);
});

function updateChart() {
  dataset.push(newNumber.value);
  chart.data.datasets[0].data = dataset;
  chart.update();
}

onBeforeUnmount(() => {
  alert("Before clear all");
  chart.destroy();
});
</script>

<template>
  <div class="chart">
    <h2 class="text-center">My Chart Data</h2>
    <canvas id="myChart"></canvas>
    <div class="mt-10">
      <input
        type="text"
        id="first_name"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        v-model="newNumber"
      />
      <button class="bg-indigo-500 p-2 mt-3" @click="updateChart()">
        Apply
      </button>
    </div>
  </div>
</template>

<style scoped>
.chart {
  width: 400px;
  height: 500px;
  background-color: rgb(147, 186, 255);
  border-radius: 10px;
  box-shadow: 2px 4px 3px black;
  margin: 30px auto;
}
</style>
