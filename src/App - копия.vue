<template>
  <div class="grid__row">

    <div v-for="(chart, i) in charts" :key="i" class="grid__col">
      <div class="box">
        <Chart :type="chart.type" :data-set="chart.data" />
        <!-- <Chart :series = "initSeries" /> -->
      </div>
    </div>

  </div>
</template>

<script>
import Chart from './components/Chart.vue'

const chartDataExemple = [
  {
    type: "pie", 
    data: {
      field1: "field 1 data - pie",
      field2: "field 2 data - pie"
    }
  },
  {
    type: "bar", 
    data: {
      field1: "field 1 data - bar",
      field2: "field 2 data - bar"
    }
  },
  {
    type: "line", 
    data: [
      {
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
      }
    ]
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
  computed : {
    /*initSeries : function() {
      return [
      {
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
      }];
    }*/
  },
  methods: {
    insertChart() {
      this.chartType = document.getElementById('chart-type').value

      if ( this.chartType !== "0" ) {        
        this.chartData = chartDataExemple.filter((data) => data.type === this.chartType)[0] 

        let chart = {
          type: this.chartType,
          //data: this.chartData
          data: [
            {
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
            }
          ]
        }

        this.charts.push(chart)
      } 

    }

  }

}
</script>

<style lang="scss" scoped>
 

</style>