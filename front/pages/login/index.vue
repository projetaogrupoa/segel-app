<template>
  <div class="body" style="display:flex;justify-content:center;align-items:center;">

    <v-card class="text-center" color="grey lighten-5" style="width:25%">
            <v-toolbar class = "logo" color="#921414">
            </v-toolbar>
            <v-card-text>
              <form ref="form">
                <v-text-field
                  v-model="user.email"
                  height="40"
                  dense
                  light
                  persistent-hint
                  :rules="[
                    (v) => !!v || 'E-mail obrigatório',
                    (v) => /.+@.+\..+/.test(v) || 'E-mail inválido',
                  ]"
                  outlined
                  @keypress.enter="login"
                >
                  <template v-slot:prepend-inner>
                    <v-tooltip bottom>
                      <template v-slot:activator="{ on }">
                        <v-icon color="#921414" v-on="on"
                          >mdi-account-outline</v-icon
                        >
                      </template>
                      Email
                    </v-tooltip>
                  </template>
                </v-text-field>

                <v-text-field
                  v-model="user.password"
                  autocomplete="password-field"
                  height="40"
                  dense
                  light
                  persistent-hint
                  :rules="[(v) => !!v || 'Senha obrigatória']"
                  :append-icon="
                    show ? 'mdi-eye-outline' : 'mdi-eye-off-outline'
                  "
                  outlined
                  :type="show ? 'text' : 'password'"
                  @click:append="show = !show"
                  @keypress.enter="login"
                >
                  <template v-slot:prepend-inner>
                    <v-tooltip bottom>
                      <template v-slot:activator="{ on }">
                        <v-icon color="#921414" v-on="on"
                          >mdi-lock-outline</v-icon
                        >
                      </template>
                      Senha
                    </v-tooltip>
                  </template>
                </v-text-field>
                <div>
                <div style="float:right">
                  <v-btn color="#921414" @click="signIn()">Acessar</v-btn>
                </div>
                <div style="float:left">
                  <v-btn to="/register" color="#A2706E">Registrar</v-btn>
                </div>
                </div>
                <br><br>
                <div
                  class="text-center justify-center"
                  style="margin-top: 10px"
                >
                  <router-link
                    to="login/forgot-password"
                    align-center
                    color="white"
                    >Esqueceu a Senha?</router-link
                  >
                </div>
              </form>
            </v-card-text>
    </v-card>
  </div>
</template>



<script>
export default {
  name: "Login",

  data() {
    return {
      user: {
        email: "",
        password: "",
      },
      show: false,
    };
  },
  methods: {
    async signIn() {

      const User = new FormData();

      User.append('username', this.user.email)
      User.append('password', this.user.password)
        
      await this.$auth
        .loginWith("local", {data: User})
        .then((response) => {
            
            this.$auth.setUser(response.data.user);
            this.$toast.success("Usuário logado!", { duration: 3000 }),
            this.$router.push("/dashboard");
    
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