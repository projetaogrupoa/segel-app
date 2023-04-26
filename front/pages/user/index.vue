<template>
  <div style="width:80%;">
    <v-row justify="end" style="margin-top: 1%">

    </v-row>
    <v-row text-color:black>
      <template v-for="user in users">

      <v-col cols="12" md="4">
        <v-card class="mx-auto" max-width="368" light>
          <v-card-title>
            {{ user.name }}
          </v-card-title>
          <v-card-subtitle>{{ user.user_type }}</v-card-subtitle>
          <v-card-text>
            <div class="text-subtitle-1">
              CPF: {{ user.cpf }}
            </div>
            <div class="text-subtitle-1">
              Telefone: {{ user.phone_number }}
            </div>
            <div class="text-subtitle-1">
              Email: {{ user.email }}
            </div>
          </v-card-text>
          </v-list-item>
          <v-divider></v-divider>
          <v-card-actions class="d-flex py-3 justify-space-between">
            <v-btn color="#A2706E" dark @click="">
              Desativar
            </v-btn>
            <v-btn color="#921414" to="/user/edit-profile" dark @click="">
              Editar
            </v-btn>
          </v-card-actions>
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
      users: [],
    }
  },
  mounted() {
    this.getUsers();  
  },
  
  methods: {
    getUsers() {
      this.$axios.get('/users/list')
        .then((response) => {
          this.users = response.data;            
        })
        .catch((error) => {
          console.log(error);
        })
    },
    handleClick(id) {
    console.log('Usuario clicado:', id)
  }
  }
}
</script>
<style scoped></style>


