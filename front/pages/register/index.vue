<template>
  <div class="body" style="display:flex;justify-content:center;align-items:center;">

    <v-card class="text-center" color="grey lighten-5" style="width:25%">
        <v-toolbar class = "logo" color="#921414">
            </v-toolbar>
            <v-card-text>
	            <form ref="form">
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
	                v-model="register.cpf"
	                color="black"
	                light
	                label="CPF"
	                variant="underlined"
	                class="v-text-field--outlined text-black"
	                outlined
	              ></v-text-field>

	              <v-text-field
	                v-model="register.phone"
	                color="black"
	                light
	                label="Telefone"
	                variant="underlined"
	                class="v-text-field--outlined text-black"
	                outlined
	              ></v-text-field>

	              <v-text-field
	                v-model="register.email"
	                color="black"
	                light
	                label="Email"
	                variant="underlined"
	                outlined
	                :rules="[
	                  (v) => !!v || 'E-mail obrigatório',
	                  (v) => /.+@.+\..+/.test(v) || 'E-mail inválido',
	                ]"
	              ></v-text-field>


	              <v-text-field
	                v-model="register.password"
	                color="black"
	                label="Senha"
	                light
	                placeholder="Enter your password"
	                variant="underlined"
	                :rules="[(v) => !!v || 'Senha obrigatória']"
	                :append-icon="show ? 'mdi-eye-outline' : 'mdi-eye-off-outline'"
	                outlined
	                :type="show ? 'text' : 'password'"
	                @click:append="show = !show"
	                @keypress.enter="login"
	              >
	              </v-text-field>  
                <div>
                <div style="float:left">
                  <v-btn to="/login" color="#A2706E">Voltar</v-btn>
                </div>
                <div style="float:right">
                  <v-btn @click="create()" color="#921414">Registrar</v-btn>
                </div>
                </div>
                <br><br>
              </form>
            </v-card-text>
    </v-card>
  </div>

</template>

<script>
export default {
  name: "Register",

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
          user_type: "1",
          available: true,
          hashed_password: this.register.password,
        })
        .then((response) => {
          console.table(response),
            this.$toast.success("Conta cadastrada com sucesso!"),
            this.$router.push("/login");
        })
        .catch(() => {});
    },
  },
};
</script>

<style scoped>
.body {
  padding: 80px;
  background-image: url("principal.jpg");
  background-position: center;
  background-repeat: no-repeat; 
  background-size: cover;
}
.logo {
  padding: 60px;
  background-image: url("logo.png");
  background-position: center;
  background-repeat: no-repeat; 
}
</style>