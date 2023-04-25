<template>
  <div class="body" style="display:flex;justify-content:center;align-items:center;">

    <v-card class="text-center" color="grey lighten-5" style="width:25%">
            <v-toolbar class = "logo" color="#921414">
            </v-toolbar>
            <v-card-text>
              <form ref="form">
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

                <div>
                <div style="float: left;">
                  <v-btn to="/login" color="#A2706E">Voltar</v-btn>
                </div>
                <div style="float: right;">
                  <v-btn to="/login" color="#921414">Enviar</v-btn>
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
  name: "ForgotPassword",
  data(){
    return{
      register:{
        email: "",
      }
    }
  }
};
</script>


<style scoped>

.text-black  {
  color: black !important;
}
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



