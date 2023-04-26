<template>
  <div style="width:80%;margin-left: 20%"> 

  <DashboardComponent />
<template v-for="area in areas">
  <v-row justify="center" style="margin:5%">
      <v-col cols="12" lg = "6">
        <v-card color="#921414"
    class="mx-auto"
  >
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      cover
    ></v-img>
    <v-card-title >
      {{ area.name }}
      <v-btn style="margin-left:2%" to="/area/edit-area" color="#A2706E">Editar</v-btn>
    </v-card-title>
    </v-card>
      </v-col>

      <v-col cols="12" lg="6">
        <v-card color="#921414">
          <v-card-item>
            <v-card-title>{{ area.name }}</v-card-title>

            <v-card-subtitle>{{ area.description }}</v-card-subtitle>
          </v-card-item>

          <v-card-text>
            <div class="text-subtitle-1">
              Iluminação: {{ area.lighting }}
            </div>
            <div class="text-subtitle-1">
              Coberto: {{ area.covered }}
            </div>
            <div class="text-subtitle-1">
              Tipo de piso: {{ area.floor_type }}
            </div>
          </v-card-text>
        </v-card>
        <div style="margin:2%">
          <div style="float:right">
            <v-btn to="/reservation/new-reservation" color="#921414" @click="">Reservar</v-btn>
          </div>
          <div style="float:left">
            <v-btn to="/dashboard" color="#A2706E">Voltar</v-btn>
          </div>
        </div>

      </v-col>
    </v-row>
  </template>

    <v-row style="margin:2%">
      <v-col cols="12" lg="12">
        <template>
          <v-layout wrap>
            <v-flex xs12 class="mb-3">
              <v-sheet height="500">
                <v-calendar ref="calendar" v-model="start" :type="type" :end="end" color="primary" light></v-calendar>
              </v-sheet>
            </v-flex>

            <v-flex sm4 xs12 class="text-sm-left text-xs-center">
              <v-btn @click="$refs.calendar.prev()" color="#921414">
                <v-icon dark left>
                  < </v-icon>
                    Anterior
              </v-btn>
            </v-flex>
            <v-flex sm4 xs12 class="text-xs-center">
              s
            </v-flex>
            <v-flex sm4 xs12 class="text-sm-right text-xs-center">
              <v-btn @click="$refs.calendar.next()" color="#921414">
                Próximo
                <v-icon right dark>
                  >
                </v-icon>
              </v-btn>
            </v-flex>
          </v-layout>
        </template>

      </v-col>
    </v-row>


  </div>
</template>

<script>
  export default {
    name: "Area",
    data() {
      return {
        areas: [],
        type: 'week',
        start: '2023-04-23',
        end: '2023-04-29',
      }
    },
    mounted() {
      this.getAreas();  
    },
    
    methods: {
      getAreas() {
        const area_id = localStorage.getItem("area_id");
        this.$axios.get('/area/list')
          .then((response) => {
            this.areas = response.data;            
          })
          .catch((error) => {
            console.log(error);
          })
      },
    }
    }
</script>


<style scoped>
.v-card {
  margin: 2%;
}
</style>
