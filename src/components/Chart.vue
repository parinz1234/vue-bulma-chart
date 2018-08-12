<template>
  <canvas :id="chartId"></canvas>
</template>
<script>
  export default {
    props: ['chartId', 'dataList'],
    methods: {
      createChart(chartId, chartData) {
        const ctx = document.getElementById(chartId);
        const myChart = new Chart(ctx, {
          type: 'line',
          data: {
            labels: chartData.labels,
            datasets: [
              {
                label: 'First',
                data: chartData.first,
                backgroundColor: 'rgba(54,73,93,.5)',
                borderColor: '#36495d',
                borderWidth: 3
              },
              {
                label: 'Second',
                data: chartData.second,
                backgroundColor: 'rgba(71, 183,132,.5)',
                borderColor: '#47b784',
                borderWidth: 3
              }
            ]
          },
          options: {
            responsive: true,
            maintainAspectRatio: false,
            lineTension: 1,
            scales: {
              yAxes: [{
                ticks: {
                  beginAtZero: true,
                  padding: 25,
                }
              }]
            }
          }
        });
      }
    },
    mounted() {
      this.createChart(this.chartId, this.dataList);
    },
    watch: {
      'dataList.first': function () {
        this.createChart(this.chartId, this.dataList);
      },
      'dataList.second': function () {
        this.createChart(this.chartId, this.dataList);
      }
    }
  }
</script>
