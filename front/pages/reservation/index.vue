<template>
    <div>
      <v-app style="background-color: white; color: white">
        <v-layout justify-center>
          <v-flex xs12 sm8 md4>
            <v-card
              class="d-flex flex-column justify-center text-center"
              color="grey lighten-5"
              max-width="344"
              title="User Registration"
            >
              <v-toolbar height="55" color="grey darken-1">
                <v-toolbar-title>Registro</v-toolbar-title>
              </v-toolbar>
              <v-container>
                <v-text-field
                  v-model="register.value"
                  color="black"
                  label="Valor"
                  light
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
  
                <v-text-field
                  v-model="register.reservation_date"
                  color="black"
                  light
                  label="Data da Reserva"
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
  
                <v-text-field
                  v-model="register.time_start"
                  color="black"
                  light
                  label="Horário de Início"
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
  
                <v-text-field
                  v-model="register.time_end"
                  color="black"
                  light
                  label="Horário de Fim"
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
  
                <v-text-field
                  v-model="register.justification"
                  color="black"
                  light
                  label="Justificativa"
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
  
  
              </v-container>
  
              <v-divider></v-divider>
  
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="grey darken-1" @click="create()">
                  Registrar
                  <v-icon icon="mdi-chevron-right" end></v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-app>
    </div>
  </template>
  
  <script>
  export default {
    name: "Register",
  
    data() {
      return {
        terms: false,
        register: {
          value: "",
          reservation_date: "",
          time_start: "",
          time_end: "",
          justification: "",
        },
        show: false,
      };
    },
    methods: {
  
      create() {
        
        this.$axios
          .$post("/reservations/create", {
            id: "",
            value: this.register.value,
            reservation_date: this.register.reservation_date,
            time_start: this.register.time_start,
            time_end: this.register.time_end,
            justification: this.register.justification,
            reservation_type: "1",
            status: str,
            area_id: str,
            account_id: str,
          })
          .then((response) => {
            console.table(response),
              this.$toast.success("Reserva cadastrada com sucesso!"),
              this.$router.push("/login");
          })
          .catch(() => {});
      },
    },
  };
  </script>
  
  <style scoped>
  </style>