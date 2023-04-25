<template>
  <div style="width:80%;margin-left: 20%;"> 
    <DashboardComponent />
<v-row text-color:black>


    <v-col cols="12" md="4">
	<v-card
    class="mx-auto"
    max-width="368"
    light
  >
  <v-card-title>
      Nome do espaço
    </v-card-title>
    <v-card-text>
      		<v-list-item-title>Tipo de reserva: Tipo </v-list-item-title>
	        <v-list-item-subtitle>Justificativa: Justificativa</v-list-item-subtitle>
		    <br>	    
		    <v-list-item-title>Responsável: Nome do usuário</v-list-item-title>
	        <v-list-item-subtitle>Tipo do usuário</v-list-item-subtitle>
	        <br>	    
		    <v-list-item-title>Data</v-list-item-title>
	        <v-list-item-subtitle>Inicio-Fim</v-list-item-subtitle>     
	        <br>    
		    <v-list-item-title>Status: status</v-list-item-title>
	        <v-list-item-subtitle>Preço: valor</v-list-item-subtitle>   
	</v-card-text>
	</v-list-item>
    <v-divider></v-divider>
    <v-card-actions class="d-flex py-3 justify-space-between">
      <v-btn color="#A2706E" dark @click="">
       	Rejeitar
      </v-btn>
      <v-btn color="#921414" dark  @click="expand = !expand">
        {{ !expand ? 'Aceitar' : 'Voltar' }}
      </v-btn>
    </v-card-actions>
        <v-expand-transition>
      <div v-if="expand">
     <v-card-actions class="d-flex py-3 justify-space-between">   
      <v-btn color="#A2706E" dark @click="">
       	Isento
      </v-btn>
      <v-btn color="#921414" dark @click="">
       	Emitir boleto
      </v-btn>
    </v-card-actions>
      </div>
    </v-expand-transition>
  </v-card>
    </v-col>


</v-row>
  </div>
</template>
 
<script>
  export default {
    data: () => ({
      expand: false,
      time: 0,

    }),
  }
</script>
  <style scoped>
  </style>