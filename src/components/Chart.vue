<template>
  <div class="chart"></div>
</template>

<script>

import Highcharts from 'highcharts'

export default {
  name: 'Chart',
  props : {
    type: String,
    dataSet : {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      target: undefined      
    }
  },
  mounted : function() {

    // Line
    if ( this.type === "line" ) {
      this.target = Highcharts.chart(this.$el, {
        title: {
          text: 'Monthly Average Temperature',
          x: -20 //center
        },
        subtitle: {
          text: 'Source: WorldClimate.com',
          x: -20
        },
        xAxis: {
          categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
          'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
        },
        yAxis: {
          title: {
            text: 'Temperature (°C)'
          },
          plotLines: [{
            value: 0,
            width: 1,
            color: '#808080'
          }]
        },
        tooltip: {
          valueSuffix: '°C'
        },
        legend: {
          layout: 'vertical',
          align: 'right',
          verticalAlign: 'middle',
              borderWidth: 0
        },
        series: this.dataSet
      })
    }

    // Pie
    if ( this.type === "pie" ) {
      this.target = Highcharts.chart(this.$el, {
        chart: {
          plotBackgroundColor: null,
          plotBorderWidth: null,
          plotShadow: false,
          type: 'pie'
        },
        title: {
          text: 'Browser market shares in January, 2018'
        },
        tooltip: {
          pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
        },
        plotOptions: {
          pie: {
            allowPointSelect: true,
            cursor: 'pointer',
            dataLabels: {
              enabled: false
            },
            showInLegend: true
          }
        },
        series: this.dataSet
      })
    }

    // Bar
    if ( this.type === "bar" ) {
      this.target = Highcharts.chart(this.$el, {
        chart: {
          type: 'bar'
        },
        title: {
          text: 'Historic World Population by Region'
        },
        subtitle: {
          text: 'Source: <a href="https://en.wikipedia.org/wiki/World_population">Wikipedia.org</a>'
        },
        xAxis: {
          categories: ['Africa', 'America', 'Asia', 'Europe', 'Oceania'],
          title: {
            text: null
          }
        },
        yAxis: {
          min: 0,
          title: {
            text: 'Population (millions)',
            align: 'high'
          },
          labels: {
            overflow: 'justify'
          }
        },
        tooltip: {
          valueSuffix: ' millions'
        },
        plotOptions: {
          bar: {
            dataLabels: {
              enabled: true
            }
          }
        },
        legend: {
          layout: 'vertical',
          align: 'right',
          verticalAlign: 'top',
          x: -40,
          y: 80,
          floating: true,
          borderWidth: 1,
          backgroundColor: ((Highcharts.theme && Highcharts.theme.legendBackgroundColor) || '#FFFFFF'),
          shadow: true
        },
        credits: {
          enabled: false
        },        
        series: this.dataSet
      })
    }

  },
  beforeDestroy: function() {
    this.target.destroy();
  }
}
</script>


<style scoped lang="scss">

  .chart {
    height: 400px;
    min-width: 386px;
    max-width: 600px;
  }  

</style>