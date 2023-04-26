<template>
  <div>
    <v-row justify="center">
      <v-card class="d-flex flex-column justify-center text-center" color="grey lighten-5">
        <v-toolbar height="55" color="#921414">
          <v-toolbar-title>Editar usuário</v-toolbar-title>
        </v-toolbar>
        <v-card-text>
          <v-container>
            <v-row>

              <v-col cols="12">
                <v-text-field v-model="register.name" color="black" label="Nome" light variant="underlined"
                  class="v-text-field--outlined text-black" outlined></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="6">
                <v-text-field v-model="register.email" color="black" light label="Email" variant="underlined" outlined
                  :rules="[
                      (v) => !!v || 'E-mail obrigatório',
                      (v) => /.+@.+\..+/.test(v) || 'E-mail inválido',
                    ]"></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="6">
                <v-text-field v-model="register.password" color="black" label="Senha" light
                  placeholder="Enter your password" variant="underlined" :rules="[(v) => !!v || 'Senha obrigatória']"
                  :append-icon="show ? 'mdi-eye-outline' : 'mdi-eye-off-outline'" outlined
                  :type="show ? 'text' : 'password'" @click:append="show = !show" @keypress.enter="login">
                </v-text-field>
              </v-col>



              <v-col cols="12" sm="4">
                <v-text-field v-model="register.cpf" color="black" light label="CPF" variant="underlined"
                  class="v-text-field--outlined text-black" outlined></v-text-field>
              </v-col>
              <v-col cols="12" sm="4">
                <v-text-field v-model="register.phone" color="black" light label="Telefone" variant="underlined"
                  class="v-text-field--outlined text-black" outlined></v-text-field>
              </v-col>
              <v-col cols="12" sm="4">
                <v-select v-model="register.covered" color="black" light label="Tipo de usuário" variant="underlined"
                  :items="['Admin', 'Tipo 1', 'Tipo 2', 'Tipo 3']" outlined disabled></v-select>
              </v-col>
            </v-row>
          </v-container>

          <div>
            <div style="float:right">
              <v-btn color="#921414" @click="">Salvar</v-btn>
            </div>
            <div style="float:left">
              <v-btn to="/user/profile" color="#A2706E">Voltar</v-btn>
            </div>
          </div>

        </v-card-text>
      </v-card>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "Register",
  layout: "menu",

  data() {
    return {
      terms: false,
      register: {
        name: "",
        cpf: "",
        email: "",
        phone: "",
        password: "",
      },
      show: false,
    };
  },
  methods: {

    create() {

      this.$axios
        .$post("/account/create", {
          id: "",
          name: this.register.name,
          cpf: this.register.cpf,
          email: this.register.email,
          phone_number: this.register.phone,
          user_type: "0",
          available: true,
          hashed_password: this.register.password,
        })
        .then((response) => {
          console.table(response),
            this.$toast.success("Conta cadastrada com sucesso!", { duration: 3000 }),
            this.$router.push("/login");
        })
        .catch(() => { });
    },
  },
};
</script>

<style scoped></style>