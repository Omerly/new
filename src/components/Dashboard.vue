<template>
  <v-app>
    <v-row>
      <v-col cols="12">
        <main class="tabla-page">
          <H1 class="text-center">Dashboard</H1>


          <v-container>

            <v-row align="center" justify="center">

              <v-col cols="4" >
                <v-card width="500" height="200" elevation="2" outlined>
             
                </v-card>
                
              </v-col>
              <v-col cols="4" >
                <v-card width="500" height="200" elevation="2" outlined>
             
                </v-card>
                
              </v-col>
              <v-col cols="4" >
                <v-card width="500" height="200" elevation="2" outlined>
             
                </v-card>
                
              </v-col>
            </v-row>
          </v-container>
          <v-container>
            <v-row align="center" justify="center">
              
              <v-col cols="6" >
                <v-card width="600" height="300" elevation="2" outlined>
                  <v-progress-circular
                    rotate="360"
                    size="150"
                    width="15"
                    value="50"
                    color="teal"
                    class="mt-2 ml-7 mb-2"
                  >
                    50%
                  </v-progress-circular>
                </v-card>
              </v-col>
              <v-col cols="6" >
                <div >
                  <v-card width="600" height="300" elevation="2" outlined>
                    <Bar
                      :chart-options="chartOptions"
                      :chart-data="chartData"
                      :chart-id="chartId"
                      :dataset-id-key="datasetIdKey"
                      :plugins="plugins"
                      :css-classes="cssClasses"
                      :styles="styles"
                      :width="width"
                      :height="height"
                    />
                  </v-card>
                </div>
              </v-col>
            </v-row>
          </v-container>

          <!--Grafica-->
        </main>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
import { Bar } from "vue-chartjs";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);

export default {
  name: "BarChart",
  components: { Bar },
  props: {
    chartId: {
      type: String,
      default: "bar-chart",
    },
    datasetIdKey: {
      type: String,
      default: "label",
    },
    width: {
      type: Number,
      default: 400,
    },
    height: {
      type: Number,
      default: 400,
    },
    cssClasses: {
      default: "",
      type: String,
    },
    styles: {
      type: Object,
      default: () => {},
    },
    plugins: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      chartData: {
        labels: [
          "Enero",
          "Febrero",
          "Marzo",
          "Abril",
          "Mayo",
          "Junio",
          "Julio",
          "Agosto",
          "Septiembre",
          "Octubre",
          "Noviembre",
          "Diciembre",
        ],
        datasets: [
          {
            label: "Lectores",
            backgroundColor: "#00FFFF",

            data: [4, 16, 25, 14, 10, 12, 30, 40, 20, 15, 35, 16],
          },
        ],
      },
      chartOptions: {
        responsive: true,
      },
    };
  },
};
</script>