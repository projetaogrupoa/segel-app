<template>
  <div style="width:80%;margin-left: 20%;">  

  <DashboardComponent />
<v-row justify="end" style="margin-top: 1%">
      <v-col cols="12"  md="3" justify="end">
      	<v-btn color="#A2706E" @click="">Filtrar</v-btn>
        <v-btn color="#921414" to="/area/new-area">Criar espaço</v-btn>
      </v-col>
</v-row>

<v-row>
    <v-col cols="12" md="4">
	<v-card color="#921414" to="/area"
    class="mx-auto"
    max-width="344"
  >
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
      cover
    ></v-img>

    <v-card-title >
      Nome do espaço
    </v-card-title>

    <v-card-subtitle>
      1,000 miles of wonder
    </v-card-subtitle>
  </v-card>
    </v-col>
</v-row>

  </div>
</template>

<style scoped>
.v-card{
	margin: 2%;
}
</style>