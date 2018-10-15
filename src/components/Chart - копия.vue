<template>
  <div></div>
</template>

<script>

import Highcharts from 'highcharts'

export default {
  name: 'Chart',
  /*props : {
    series : {
      type: Array,
      required: true
    }
  },*/
  props: {
    type: String,
    dataSet: {
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
      dataSet: this.dataSet
    });
  },
  beforeDestroy: function() {
    this.target.destroy();
  }
}
</script>


<style scoped lang="scss">
  
  .chart {

    &__container {

    }

    &__item {
      min-width: 310px;
      height: 400px;
      max-width: 600px;
      margin: 0 auto
    }

  }

</style>