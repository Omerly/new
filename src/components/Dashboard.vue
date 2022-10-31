<template>
  <v-app>
      <v-row>

          <v-col cols="12">

              <main class="tabla-page">
                  <H1 class="text-center">Dashboard</H1>
                  <!--Grafica-->
                  <div class="grafica">
                      <Bar :chart-options="chartOptions" :chart-data="chartData" :chart-id="chartId"
                          :dataset-id-key="datasetIdKey" :plugins="plugins" :css-classes="cssClasses" :styles="styles"
                          :width="width" :height="height" />

                  </div>

                  <div class="grafica2">




                  </div>





              </main>

          </v-col>

      </v-row>
  </v-app>
</template>
<style>
.grafica,
.grafica2 {

  max-width: 600px;

}

</style>
<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  props: {
    chartId: {
      type: String,
      default: 'bar-chart'
    },
    datasetIdKey: {
      type: String,
      default: 'label'
    },
    width: {
      type: Number,
      default: 400
    },
    height: {
      type: Number,
      default: 400
    },
    cssClasses: {
      default: '',
      type: String
    },
    styles: {
      type: Object,
      default: () => { }
    },
    plugins: {
      type: Object,
      default: () => { }
    }
  },
  data() {
    return {
      chartData: {
        labels: ['Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre'],
        datasets: [{
          label: 'Lectores',
          backgroundColor: '#00FFFF',


          data: [10, 12, 30, 40, 20, 15]
        }]
      },
      chartOptions: {
        responsive: true
      }
    }
  }
}
</script>

