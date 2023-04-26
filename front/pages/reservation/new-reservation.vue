<template>
  <div style="margin-top:5%">
    <v-row justify="center">
      <v-card class="d-flex flex-column justify-center text-center" color="grey lighten-5">
        <v-toolbar height="55" color="#921414">
          <v-toolbar-title>Solicitação de reserva</v-toolbar-title>
        </v-toolbar>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="6">
                <v-select v-model="register.lights" color="black" light label="Espaço" variant="underlined"
                  :items="['Campo A', 'Campo B', 'etc']" outlined disabled></v-select>
              </v-col>
              <v-col cols="12" sm="6" md="6">
                <v-select v-model="register.type" color="black" light label="Tipo" variant="underlined"
                  :items="['Aula', 'Pesquisa/Extenção', 'Outros']" outlined></v-select>
              </v-col>

              <v-col cols="12">

                <v-text-field v-model="register.justification" color="black" light label="Justificativa"
                  variant="underlined" class="v-text-field--outlined text-black" outlined></v-text-field>

              </v-col>

              <v-col cols="12" sm="4">
                <v-text-field v-model="register.reservation_date" color="black" light label="Data da Reserva"
                  variant="underlined" class="v-text-field--outlined text-black" type="date" outlined></v-text-field>
              </v-col>
              <v-col cols="12" sm="4">
                <v-text-field v-model="register.time_start" color="black" light label="Horário de Início" variant="underlined"
                  class="v-text-field--outlined text-black" outlined type="time"></v-text-field>
              </v-col>
              <v-col cols="12" sm="4">
                <v-text-field v-model="register.time_end" color="black" light label="Horário de Fim"
                  variant="underlined" class="v-text-field--outlined text-black" outlined type="time"></v-text-field>
              </v-col>

            </v-row>
          </v-container>

          <div>
            <div style="float:right">
              <v-btn color="#921414" @click="create()">Solicitar</v-btn>
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
  name: "Register",
  layout: "menu",

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
      const user_id = localStorage.getItem("user");
      const area_id = localStorage.getItem("area_id");
      this.$axios
        .$post("/reservation/create", {
          id: "",
          reservation_date: this.register.reservation_date,
          time_start: this.register.time_start,
          time_end: this.register.time_end,
          justification: this.register.justification,
          reservation_type: this.register.type,
          area_id: area_id,
          account_id: user_id,
        })
        .then((response) => {
          console.table(response),
            this.$toast.success("Reserva cadastrada com sucesso!", { duration: 3000 }),
            this.$router.push("/dashboard");
        })
        .catch(() => { });
    },
  },
};
</script>
  
<style scoped></style>
