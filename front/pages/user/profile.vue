<template>
  <div> 

  <DashboardComponent />

<v-row justify="center" style="margin:5%">
  <v-col cols="12" lg = "12">
    <v-card color="#921414">
      <v-card-item>
        <v-card-title>Nome do usuário</v-card-title>

        <v-card-subtitle>Tipo</v-card-subtitle>
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
                  <v-btn to="/user/edit-profile"color="#921414" @click="">Editar</v-btn>
                </div>
                <div style="float:left">
                  <v-btn to="/dashboard" color="#A2706E">Voltar</v-btn>
                </div>
                </div>

    </v-col>
    <v-row text-color:black>
<v-col cols="12" lg = "12">
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
  </v-col>

</v-row>
    </v-row>

   <v-row  style="margin:2%">
    <v-col cols="12" lg = "12">

    </v-col>
    </v-row>


  </div>
</template>
﻿

<style scoped>
.v-card{
  margin: 2%;
}
</style>
