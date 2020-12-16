<template>
 <div>
     <VueApexCharts :width="data.width" :height="data.chartOptions.chart.height" :type="data.chartOptions.chart.type" :options="data.chartOptions" :series="data.series"></VueApexCharts>

 </div>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'

export default {
  name: 'mychart',
  components:{VueApexCharts},
  data: function() {
    return {
     
    }
  },
  props:['data']
}
</script>


