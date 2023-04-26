<template>
  <div style="width:80%;margin-left: 20%;">
    <v-row justify="end" style="margin-top: 1%">
      <v-col cols="12" md="12" justify="end">
        <v-btn color="#921414" to="/alugueis/paid">Concluídas</v-btn>
        <v-btn color="#A2706E" to="/alugueis/awaiting-payment">Aguardando pagamento</v-btn>
        <v-btn color="#A2706E" to="/alugueis/paid">Rejeitadas</v-btn>
      </v-col>
    </v-row>
    <v-row text-color:black>

      <v-col cols="12" md="4">
        <v-card class="mx-auto" max-width="368" light>
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