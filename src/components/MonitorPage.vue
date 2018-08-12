<template>
  <div>
    <div class="columns">
      <div class="column is-one-third">
        <!-- TABLE -->
        <Table
          :dataList="table"
          />
      </div>
      <div class="column">
        <div class="columns right-content">
          <div class="column">
            <!-- GRAPH -->
            <Chart
              :dataList="application"
              chartId="application-chart"
              />
          </div>
          <div class="column">
            <!-- GRAPH -->
            <Chart
              :dataList="analytic"
              chartId="analytic-chart"
              />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import Table from './Table'
  // import ApplicationChart from './ApplicationChart'
  // import AnalyticChart from './AnalyticChart'
  import Chart from './Chart'
  export default {
    components: {
      Table,
      Chart
    },
    data: () => ({
      table: [],
      analytic: {
        labels: [],
        first: [],
        second: []
      },
      application: {
        labels: [],
        first: [],
        second: []
      }
    }),
    created () {
      // this.randomTable()
      // this.randomAnalytic()
      setInterval(() => {
        this.randomTable()
        this.randomAnalytic()
        this.randomApplication()
      }, 5000)
    },
    methods: {
      randomTable () {
        this.table = Array(35).fill().map((value, index) => ({
          id: index + 1,
          title: Math.round(Math.random() * 10),
          value: Math.round(Math.random() * 10)
        }))
      },
      randomAnalytic () {
        this.analytic.labels = Array(31).fill().map((value, index) => index + 1)
        this.analytic.first = Array(31).fill().map(() => Math.round(Math.random() * 10))
        this.analytic.second = Array(31).fill().map(() => Math.round(Math.random() * 10))
      },
      randomApplication () {
        this.application.labels = Array(31).fill().map((value, index) => index + 1)
        this.application.first = Array(31).fill().map(() => Math.round(Math.random() * 10))
        this.application.second = Array(31).fill().map(() => Math.round(Math.random() * 10))
      }
    }
  }
</script>
<style lang="scss" scoped>
  .right-content {
    height: 100%;
    flex-direction: column;
    .column {
      height: 50%;
    }
  }
</style>

