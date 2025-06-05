<script setup>
import { Bar } from 'vue-chartjs'
import { Chart, BarElement, CategoryScale, LinearScale, LogarithmicScale, Tooltip, Legend } from 'chart.js'
import ChartDataLabels from 'chartjs-plugin-datalabels'

Chart.register(BarElement, CategoryScale, LinearScale, LogarithmicScale, Tooltip, Legend, ChartDataLabels)

const props = defineProps({
  data: Object,
  options: Object
})
</script>

<template>
  <Bar :data="data" :options="options" />
</template> 