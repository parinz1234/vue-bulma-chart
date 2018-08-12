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
            <AnalyticChart
              :dataList="analytic"
              />
          </div>
          <div class="column">
            <!-- GRAPH -->
            <ApplicationChart />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import Table from './Table'
  import ApplicationChart from './ApplicationChart'
  import AnalyticChart from './AnalyticChart'
  export default {
    components: {
      Table,
      ApplicationChart,
      AnalyticChart
    },
    data: () => ({
      table: [],
      analytic: {
        labels: [],
        first: [],
        second: []
      },
      application: []
    }),
    created () {
      this.randomTable()
      this.randomAnalytic()
      setInterval(() => {
        this.randomTable()
        this.randomAnalytic()
        // console.log(this.analytic)
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

