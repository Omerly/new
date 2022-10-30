<template>
    <v-app>
      <v-row>

            <v-col cols="12">

                <main class="tabla-page">
                    <H1 class="text-center">Dashboard</H1>
                    <!--Grafica-->


<template>
  <v-card
    class="mt-4 mx-auto"
    max-width="400"
  >
    <v-sheet
      class="v-sheet--offset mx-auto"
      color="teal"
      elevation="12"
      max-width="calc(100% - 32px)"
    >
      <v-sparkline
        :labels="labels"
        :value="value"
        color="white"
        line-width="2"
        padding="16"
      ></v-sparkline>
    </v-sheet>

    <v-card-text class="pt-0">
      <div class="text-h6 font-weight-light mb-2">
        Registro de usuarios
      </div>
      
      <v-divider class="my-2"></v-divider>
      <v-icon
        class="mr-2"
        small
      >
        mdi-clock
      </v-icon>
      <span class="text-caption grey--text font-weight-light">Último registro hace 26 minutos</span>
    </v-card-text>
  </v-card>
</template>
                    

                </main>

            </v-col>

        </v-row>
    </v-app>
</template>


<Style>
.grafica 
{
   height:20px;
   width:10px;
}


</Style>
    
  
<script>
  export default {
    data: () => ({
      labels: [
        '12am',
        '3am',
        '6am',
        '9am',
        '12pm',
        '3pm',
        '6pm',
        '9pm',
      ],
      value: [
        200,
        675,
        410,
        390,
        310,
        460,
        250,
        240,
      ],
    }),
  }
</script>

<style>
  .v-sheet--offset {
    top: -24px;
    position: relative;
  }
</style>


