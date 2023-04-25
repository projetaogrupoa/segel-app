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
                  v-model="register.name"
                  color="black"
                  label="Nome"
                  light
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
  
                <v-text-field
                  v-model="register.description"
                  color="black"
                  light
                  label="Descrição"
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
    name: "Register Area",
  
    data() {
      return {
        terms: false,
        register: {
          name: "",
          description: "",
        },
        show: false,
      };
    },
    methods: {
  
      create() {
        
        this.$axios
          .$post("/area/create", {
            id: "",
            name: this.register.name,
            description: this.register.cpf,
            available: true,
            account_id: ""
          })
          .then((response) => {
            console.table(response),
              this.$toast.success("Área cadastrada com sucesso!"),
              this.$router.push("/login");
          })
          .catch(() => {});
      },
    },
  };
  </script>
  
  <style scoped>
  </style>