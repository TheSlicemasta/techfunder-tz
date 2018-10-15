<template>
  <div class="grid__row">

    <div v-for="(chart, i) in charts" :key="i" class="grid__col">
      <div class="box chart__container">
        <Chart :type="chart.type" :data-set="chart.data" />
      </div>
    </div>

  </div>
</template>

<script>
import Chart from './components/Chart.vue'

const chartDataExemple = [
  {
    type: "pie", 
    data: [{
    name: 'Brands',
    colorByPoint: true,
    data: [{
      name: 'Chrome',
      y: 61.41,
      sliced: true,
      selected: true
      }, {
        name: 'Internet Explorer',
        y: 11.84
      }, {
        name: 'Firefox',
        y: 10.85
      }, {
        name: 'Edge',
        y: 4.67
      }, {
        name: 'Safari',
        y: 4.18
      }, {
        name: 'Other',
        y: 7.05
      }]
    }]
  },
  {
    type: "bar", 
    data: [{
        name: 'Year 1800',
        data: [107, 31, 635, 203, 2]
      }, {
        name: 'Year 1900',
        data: [133, 156, 947, 408, 6]
      }, {
        name: 'Year 2000',
        data: [814, 841, 3714, 727, 31]
      }, {
        name: 'Year 2016',
        data: [1216, 1001, 4436, 738, 40]
      }
    ]
  },
  {
    type: "line", 
    data: [{
          name: 'Tokyo',
          data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2, 26.5, 23.3, 18.3, 13.9, 9.6]
      }, {
          name: 'New York',
          data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8, 24.1, 20.1, 14.1, 8.6, 2.5]
      }, {
          name: 'Berlin',
          data: [-0.9, 0.6, 3.5, 8.4, 13.5, 17.0, 18.6, 17.9, 14.3, 9.0, 3.9, 1.0]
      }, {
          name: 'London',
          data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0, 16.6, 14.2, 10.3, 6.6, 4.8]
      }]
  }
]

export default {
  name: 'app',
  components: {
    Chart
  },
  data() {
    return {
      charts: [],
      chartType: '',
      chartData: []
    }
  },
  created() {
    document.getElementById('chart-insert').addEventListener('click', () => {
      this.insertChart()
    })
  },
  methods: {
    insertChart() {
      this.chartType = document.getElementById('chart-type').value

      if ( this.chartType !== "0" ) {        
        this.chartData = chartDataExemple.filter((data) => data.type === this.chartType)[0].data 

        let chart = {
          type: this.chartType,
          data: this.chartData
        }

        this.charts.push(chart)
      } 

    }

  }

}
</script>

<style lang="scss" scoped>

  .chart__container {
    background: none #fff;

    &:before {
      display: none;
    }
  } 

</style>