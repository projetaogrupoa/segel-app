<template>
  <div style="width:80%;margin-left: 20%;">  

  <DashboardComponent />
  <v-row justify="end" style="margin-top: 1%">
        <v-col cols="12"  md="2" justify="end">
          <v-btn color="#921414" to="/area/new-area">Criar espaço</v-btn>
        </v-col>
  </v-row>
<v-row>    
  <template v-for="area in areas">
    <v-col cols="12" md="4">
      <v-card color="#921414" to="/area" class="mx-auto" max-width="344" @click.native="getAreaId(area.id)">
        <v-img src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg" height="200px" cover></v-img>
        <v-card-title>
          <div>{{ area.name }}</div>
        </v-card-title>
        <v-card-subtitle>{{ area.description }}</v-card-subtitle>
      </v-card>
    </v-col>    
    </template>

  </v-row>

  </div>
</template>

<script>
  export default {
    name: "Area",
    data() {
      return {
        areas: [],
      }
    },
    mounted() {
      this.getAreas();  
    },
    
    methods: {
      getAreas() {
        this.$axios.get('/area/list')
          .then((response) => {
            this.areas = response.data;            
          })
          .catch((error) => {
            console.log(error);
          })
      },
      getAreaId(area_id) {
      console.log('Espaço clicado:', area_id);
      localStorage.setItem("area_id", area_id);
    }
    }
  }
</script>

<style scoped>
.v-card{
  margin: 2%;
}
</style>