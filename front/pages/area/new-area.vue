<template>
  <div>
  <DashboardComponent />
  <v-row justify="center">
      <v-card class="d-flex flex-column justify-center text-center"
              color="grey lighten-5">
        <v-toolbar height="55" color="#921414">
                <v-toolbar-title>Novo Espaço</v-toolbar-title>
        </v-toolbar>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="6"
                md="6"
              >
                <v-text-field
                  v-model="register.name"
                  color="black"
                  label="Nome"
                  light
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="6"
              >

              <v-text-field
                v-model="register.photo_url"
                label="URL da imagem"
                light
                variant="underlined"
                prepend-icon="mdi-camera"
                class="v-text-field--outlined text-black"
                outlined
              ></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-text-field
                  v-model="register.description"
                  color="black"
                  light
                  label="Descrição"
                  variant="underlined"
                  class="v-text-field--outlined text-black"
                  outlined
                ></v-text-field>
              </v-col>

              <v-col
                cols="12"
                sm="3"
              >
                <v-select
                  v-model="register.available"
                  color="black"
                  light
                  label="Disponível"
                  variant="underlined"
                  :items="['Sim', 'Não']"
                  outlined
                ></v-select>
              </v-col>
              <v-col
                cols="12"
                sm="3"
              >
                <v-select
                  v-model="register.flooring"
                  color="black"
                  light
                  label="Tipo de piso"
                  variant="underlined"
                  :items="['Grama', 'Asfalto', 'Poliuretano', 'Outros']"
                  outlined
                ></v-select>
              </v-col>
              <v-col
                cols="12"
                sm="3"
              >
                <v-select
                  v-model="register.covered"
                  color="black"
                  light
                  label="Coberto"
                  variant="underlined"
                  :items="['Sim', 'Não']"
                  outlined
                ></v-select>
              </v-col>
              <v-col
                cols="12"
                sm="3"
              >
                <v-select
                  v-model="register.lights"
                  color="black"
                  light
                  label="Iluminação"
                  variant="underlined"
                  :items="['Sim', 'Não']"
                  outlined
                ></v-select>
              </v-col>
            </v-row>
          </v-container>

          <div>
                <div style="float:right">
                  <v-btn color="#921414" @click="create()">Criar</v-btn>
                </div>
                <div style="float:left">
                  <v-btn to="/dashboard" color="#A2706E">Voltar</v-btn>
                </div>
          </div>

        </v-card-text>


      </v-card>
  </v-row>
  </div>
</template>

<script>
  export default {
    name: "Area",
  
    data() {
      return {
        terms: false,
        register: {
          name: "",
          photo_url: "",
          description: "",
          available: "",
          flooring: "",
          covered: "",
          lights: "",
        },
        show: false,
      };
    },
    methods: {
  
      create() {
        const user_id = localStorage.getItem("user");
        this.$axios
          .$post("/area/create", {
            id: "",
            name: this.register.name,
            photo_url: this.register.photo_url,
            description: this.register.description,
            available: this.register.available === 'Sim',
            floor_type: this.register.flooring,
            covered: this.register.covered,
            lighting: this.register.lights,
            account_id: user_id,
          })
          .then((response) => {
            console.table(response),
              this.$toast.success("Área cadastrada com sucesso!", { duration: 3000 }),
              this.$router.push("/login");
          })
          .catch(() => {});
      },
    },
  };
  </script>

  <style scoped>
  </style>
