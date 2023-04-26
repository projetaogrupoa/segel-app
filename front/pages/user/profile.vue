<template>
  <div>
    <v-row justify="center">
      <v-col cols="12" lg="12">
        <v-card color="#921414">
          <v-card-item>
            <v-card-title>nome</v-card-title>

            <v-card-subtitle>tipo de usuario</v-card-subtitle>
          </v-card-item>

          <v-card-text>
            <div class="text-subtitle-1">
              CPF: cpf
            </div>
            <div class="text-subtitle-1">
              Telefone: telefone
            </div>
            <div class="text-subtitle-1">
              Email: email
            </div>
          </v-card-text>
        </v-card>
        <div style="margin:2%">
          <div style="float:right">
            <v-btn to="/user/edit-profile" color="#921414" @click="">Editar</v-btn>
          </div>
          <div style="float:left">
            <v-btn to="/dashboard" color="#A2706E">Voltar</v-btn>
          </div>
        </div>

      </v-col>
      
    </v-row>
    <v-row justify="center">
      <template v-for="reservation in reservations">
        <v-col cols="12" lg="12">
          <v-col cols="12" md="4">
            <v-card class="mx-auto" max-width="368" light>
              <v-card-title>
                {{ reservation.area_id }}
              </v-card-title>
              <v-card-text>
                <v-list-item-title>Tipo de reserva: {{ reservation.reservation_type }} </v-list-item-title>
                <v-list-item-subtitle>Justificativa: {{ reservation.justification }}</v-list-item-subtitle>
                <br>
                <v-list-item-title>{{ reservation.reservation_date }}</v-list-item-title>
                <v-list-item-subtitle>{{ reservation.time_start }}-{{ reservation.time_end }}</v-list-item-subtitle>     
                <br>    
                <v-list-item-title>Status: {{ reservation.status }}</v-list-item-title>
                <v-list-item-subtitle>Preço: valor</v-list-item-subtitle>
              </v-card-text>
              <v-divider></v-divider>
            </v-card>
          </v-col>
        </v-col>
      </template>

      </v-row>

    <v-row style="margin:2%">
      <v-col cols="12" lg="12">

      </v-col>
    </v-row>


  </div>
</template>

<script>
export default {
  layout: "menu",
  data() {
    return {
      users: {},
      reservations: [],
    }
  },
  mounted() {
    
    this.getUsers();  
    this.getReservations();
  },
  
  methods: {
    getUsers() {
      const cpf_user = localStorage.getItem("cpf");
      this.$axios.get('/users/list', {
        params: {
            cpf: cpf_user
        }
      })
        .then((response) => {
          this.users = response.data;            
        })
        .catch((error) => {
          console.log(error);
        })
    },

    getReservations() {
        const user_id = localStorage.getItem("user");
        this.$axios.get('/reservation/list', {
        params: {
            account_id: user_id
        }
      })
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

<style scoped>
  .v-card{
    margin: 2%;
}
</style>
