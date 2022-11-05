<template>
  <v-app
    ><!--Barra IZQUIERDA-->
    <v-layout row>
      <v-flex md8>
        <v-app>
          <v-container>
            <v-row>
              <v-col cols="12" sm="12">
                <v-app-bar flat class="mx-8 mb-8 mt-3">
                  <!--BARRA DE BUSQUEDA-->
                  <v-text-field
                    label="Buscar"
                    prepend-icon="mdi-map-marker"
                    color="white"
                    flat
                    success
                  ></v-text-field>
                  <v-spacer></v-spacer>
                  <!--BARRA DE HORARIO-->
                  <v-chip class="ma-2">
                    
                    Sabado 5, Noviembre 18:30 PM
                  </v-chip>
                </v-app-bar>
              </v-col>

              <v-col cols="12" sm="6">
                <!--GRAFICOS DE BARRAS-->
                <v-card
                  width="600"
                  height="220"
                  elevation="2"
                  outlined
                  class="rounded-lg"
                >
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
              </v-col>

              <v-col cols="12" sm="6">
                <!--GRAFICOS-->

                <v-card
                  width="350"
                  height="220"
                  elevation="2"
                  outlined
                  class="rounded-lg"
                >
                  <v-app-bar class="mt-0.5 ma-4 rounded-lg">
                    <h5>Mis Libros</h5>

                    <v-btn class="ml-4" color="teal" rounded dark depressed>
                      Semana
                    </v-btn>
                    <v-btn class="ml-4" text> Mes </v-btn>
                  </v-app-bar>

                  <v-progress-circular
                    rotate="360"
                    size="90"
                    width="15"
                    value="70"
                    color="teal"
                    class="mt-n2 ml-5 mb-2"
                  >
                    70%
                  </v-progress-circular>
                  Leido

                  <v-progress-circular
                    rotate="360"
                    size="90"
                    width="15"
                    value="30"
                    color="red"
                    class="mt-n2 ml-5 mb-2"
                  >
                    30%
                  </v-progress-circular>
                  No Leido
                </v-card>
              </v-col>
              <!--LIBROS VISTOS-->
              <v-col>
                <v-card
                 
                  elevation="2"
                  outlined
                  class="rounded-lg"
                >
                <!--TABLA-->
                  <v-simple-table dark>
                    <template v-slot:default>
                      <thead>
                        <tr>
                          <th class="text-left">Nombre del Libro</th>
                          <th class="text-left">Cantidad de veces leido</th>
                        </tr>
                      </thead>
                      <tbody>
                        <tr v-for="item in desserts" :key="item.name">
                          <td>{{ item.name }}</td>
                          <td>{{ item.cant }}</td>
                        </tr>
                      </tbody>
                    </template>
                  </v-simple-table>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-app>
      </v-flex>
      <!--BARRA DERECHA-->
      <v-flex md4>
        <v-app style="background: black">
          <v-container>
            <v-row>
              <v-col cols="12" sm="12">
                <v-list two-line>
                  <!--Lista de Libros-->
                  <v-card class="mx-auto" max-width="500">
                    <v-toolbar color="teal" dark>
                      <v-app-bar-nav-icon></v-app-bar-nav-icon>

                      <v-toolbar-title
                        ><v-list-item>
                          <v-list-item-content>
                            <v-list-item-title align="center">
                              John Lincon
                            </v-list-item-title>
                            <v-list-item-subtitle class="teal--text">
                              25 años, Venezuela
                            </v-list-item-subtitle>
                          </v-list-item-content>
                          <v-list-item-avatar>
                            <img
                              src="https://cdn.vuetifyjs.com/images/john.jpg"
                              alt="John"
                            />
                          </v-list-item-avatar>
                          <v-space></v-space> </v-list-item
                      ></v-toolbar-title>

                      <v-spacer></v-spacer>
                    </v-toolbar>

                    <v-list>
                      <v-list-group
                        v-for="item in items"
                        :key="item.title"
                        v-model="item.active"
                        :prepend-icon="item.action"
                        no-action
                      >
                        <template v-slot:activator>
                          <v-list-item-content>
                            <v-list-item-title
                              v-text="item.title"
                            ></v-list-item-title>
                          </v-list-item-content>
                        </template>

                        <v-list-item
                          v-for="child in item.items"
                          :key="child.title"
                        >
                          <v-list-item-content>
                            <v-list-item-title
                              v-text="child.title"
                            ></v-list-item-title>
                          </v-list-item-content>
                        </v-list-item>
                      </v-list-group>
                    </v-list>
                  </v-card>
                </v-list>
              </v-col>
            </v-row>
          </v-container>
        </v-app>
      </v-flex>
    </v-layout>
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
//SCRIPT DE LA GRAFICA DE BARRAS
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
      //SCRIPT DE LA GRAFICA DE BARRAS
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
      //SCRIPT DE LA LISTA
      items: [
        {
          action: "mdi-ticket",
          items: [{ title: "Novela Literaria" }],
          title: "Literatura",
        },
        {
          action: "mdi-silverware-fork-knife",
          active: true,
          items: [
            { title: "Ciencia Ficción" },
            { title: "Manga" },
            { title: "Terror" },
          ],
          title: "Cómic y Fantasía",
        },
        {
          action: "mdi-school",
          items: [{ title: "Cómic y manga infantil" }],
          title: "Infantil",
        },
        {
          action: "mdi-human-male-female-child",
          items: [{ title: "Cómic Juvenil" }],
          title: "Juvenil",
        },
        {
          action: "mdi-bottle-tonic-plus",
          items: [{ title: "Historia" }],
          title: "Conocimiento y Ciencia",
        },
        {
          action: "mdi-briefcase",
          items: [{ title: "Economía" }],
          title: "Actualidad y Empresa",
        },
        {
          action: "mdi-tag",
          items: [{ title: "Cocina vegetariana y vegana" }],
          title: "Cocina y Gastronomía",
        },
        {
          action: "mdi-tag",
          items: [{ title: "Estilo de vida" }],
          title: "Bienestar y Salud",
        },
        {
          action: "mdi-tag",
          items: [{ title: "Ocio y entretenimiento" }],
          title: "Viajes y ocio",
        },
        {
          action: "mdi-tag",
          items: [{ title: "Agendas" }],
          title: "Agendas y Calendarios",
        },
        {
          action: "mdi-tag",
          items: [{ title: "Parque Botanico" }],
          title: "Naturaleza",
        },
      ],
//SCRIPT DE LA TABLA
      desserts: [
        {
          name: "Novela Literaria",
          cant: 2,
        },
        {
          name: "Ciencia Ficción",
          cant: 1,
        },
        {
          name: "Manga",
          cant: 3,
        },
        {
          name: "Terror",
          cant: 5,
        },
        {
          name: "Cocina vegetariana y vegana",
          cant: 2,
        },
        {
          name: "Estilo de vida",
          cant: 1,
        },
        {
          name: "Economía",
          cant: 1,
        },
        {
          name: "Ocio y entretenimiento",
          cant: 1,
        },
        {
          name: "Agendas",
          cant: 1,
        },
        {
          name: "Parque Botanico",
          cant: 3,
        },
      ],
    };
  },
};
</script>
