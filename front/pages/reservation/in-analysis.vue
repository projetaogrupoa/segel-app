<template>
  <div style="width:80%;">
    <v-row justify="end" style="margin-top: 1%">
      <v-col cols="12" md="12" justify="end">
        <v-btn color="#A2706E" to="/reservation/done">Concluídas</v-btn>
        <v-btn color="#921414" to="/reservation/in-analysis">Em análise</v-btn>
        <v-btn color="#921414" to="/reservation/rejected">Rejeitadas</v-btn>
      </v-col>
</v-row>
<template v-for="reservation in reservations">
  <v-row text-color:black>

      <v-col cols="12" md="4">
    <v-card
      class="mx-auto"
      max-width="368"
      light
    >
    <v-card-title>
        {{ reservation.area_id }} 
      </v-card-title>
      <v-card-text>
            <v-list-item-title>Tipo de reserva: {{ reservation.reservation_type }} </v-list-item-title>
            <v-list-item-subtitle>Justificativa: {{ reservation.justification }}</v-list-item-subtitle>
          <br>	    
          <v-list-item-title>Responsável: {{ reservation.account_id }}</v-list-item-title>
            <v-list-item-subtitle>Tipo do usuário</v-list-item-subtitle>
            <br>	    
          <v-list-item-title>{{ reservation.reservation_date }}</v-list-item-title>
            <v-list-item-subtitle>{{ reservation.time_start }}-{{ reservation.time_end }}</v-list-item-subtitle>     
            <br>    
          <v-list-item-title>Status: {{ reservation.status }}</v-list-item-title>
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
</template>
  </div>
</template>
 
<script>
  export default {
    data: () => {
      return {
        reservations: [],
      }
    },
    mounted() {
      this.getReservations();  
    },

    methods: {
      getReservations() {
        this.$axios.get('/reservation/list')
          .then((response) => {
            this.reservations = response.data;            
          })
          .catch((error) => {
            console.log(error);
          })
      },
    }
  }
</script>
<style scoped></style>