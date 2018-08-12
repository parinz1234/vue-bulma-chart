<template>
  <div>
    <canvas id="analytic-chart"></canvas>
  </div>
</template>
<script>
  import planetChartData from './chart-data';
  export default {
    data () {
      return {
        planetChartData: planetChartData
      }
    },
    methods: {
      createChart(chartId, chartData) {
        const ctx = document.getElementById(chartId);
        const myChart = new Chart(ctx, {
          type: chartData.type,
          data: chartData.data,
          options: chartData.options,
        });
      }
    },
    mounted() {
      this.createChart('analytic-chart', this.planetChartData);
    }
  }
</script>
