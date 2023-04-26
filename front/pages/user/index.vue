<template>
  <div style="width:80%;margin-left: 20%;">
    <v-row justify="end" style="margin-top: 1%">

    </v-row>
    <v-row text-color:black>

      <v-col cols="12" md="4">
        <v-card class="mx-auto" max-width="368" light>
          <v-card-title>
            Nome do usuario
          </v-card-title>
          <v-card-subtitle>Tipo</v-card-subtitle>
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


    </v-row>
  </div>
</template>
 
<script>
export default {
  layout: "menu",

  data: () => ({
    expand: false,
    time: 0,

  }),
}
</script>
<style scoped></style>