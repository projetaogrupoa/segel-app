<template>
  <div style="width:80%;margin-left: 20%;">  

  <DashboardComponent />
  <v-row justify="end" style="margin-top: 1%">
        <v-col cols="12"  md="3" justify="end">
          <v-btn color="#A2706E" @click="">Filtrar</v-btn>
          <v-btn color="#921414" to="/area/new-area">Criar espaço</v-btn>
        </v-col>
  </v-row>
  <template v-for="area in areas">
  <v-row>      
    <v-col cols="12" md="4">
      <v-card color="#921414" to="/area" class="mx-auto" max-width="344" @click.native="handleClick(area.name)">
        <v-img src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg" height="200px" cover></v-img>
        <v-card-title>
          <div>{{ area.name }}</div>
        </v-card-title>
        <v-card-subtitle>{{ area.description }}</v-card-subtitle>
      </v-card>
    </v-col>    
  </v-row>
</template>

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
      handleClick(name) {
      console.log('Espaço clicado:', name);
      this.$router.push({ name: 'area/', params: { name: name }});
    }
    }
  }
</script>

<style scoped>
.v-card{
	margin: 2%;
}
</style>