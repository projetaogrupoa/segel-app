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
        { title: "Minha Conta", icon: "mdi-account", routa: "/account" },
        { title: "Reservas", icon: "mdi-package", route: "/reservation" },
        { title: "Clientes", icon: "mdi-account-group" },
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