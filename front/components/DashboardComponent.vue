<template>
  <div>
    <v-navigation-drawer
      absolute
      v-model="drawer"
      permanent
      color="primary"
    >
      <v-list-item class="logo">
      </v-list-item>

      <v-divider></v-divider>
      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-img src="https://randomuser.me/api/portraits/men/85.jpg"></v-img>
        </v-list-item-avatar>

        <v-list-item-title>Nome nome</v-list-item-title>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item v-for="item in items" :key="item.title" link :to="item.route">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      drawer: true,
      items: [
        { title: "Início", icon: "mdi-home-city", route: "/dashboard" },
        { title: "Meu Perfil", icon: "mdi-account", route: "/user/profile" },
        { title: "Area", icon: "mdi-home-outline", route: "/area"},
        { title: "Adicionar Area", icon: "mdi-home-plus-outline", route: "/area/new-area"},
        { title: "Editar Area", icon: "mdi-home-edit-outline", route: "/area/edit-area"},
        { title: "Reservas", icon: "mdi-calendar-clock", route: "/reservation" },
        { title: "Nova Reserva", icon: "mdi-calendar-plus", route: "/reservation/new-reservation" },
        { title: "Reservas em Análise", icon: "mdi-calendar-alert", route: "/reservation/in-analysis" },
        { title: "Reservas Canceladas", icon: "mdi-calendar-remove", route: "/reservation/rejected" },
        { title: "Reservas Finalizadas", icon: "mdi-calendar-check", route: "/reservation/done" },
        { title: "Alugueis Aguardando Pagamento", icon: "mdi-receipt-text-clock", route: "/alugueis/awaiting-payment" },
        { title: "Alugueis Pagos", icon: "mdi-receipt-text-check", route: "/alugueis/paid" },
        { title: "Alugueis Cancelados", icon: "mdi-receipt-text-remove", route: "/alugueis/cancelled" },
        { title: "Usuários", icon: "mdi-account-group", route: "/user" },
        { title: "Sair", icon: "mdi-logout", route: "/login" }
      ],
      mini: true,
    };
  },
};
</script>

<style scoped>
.logo {
  background-image: url("logo.png");
  background-repeat: no-repeat;
  background-position: center;
  height: 15%;
}
</style>