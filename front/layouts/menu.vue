<template>
  <v-app>
    <DashboardComponent />
    <v-main class="main-content">
      <v-container fluid>
        <nuxt-child />
      </v-container>
    </v-main>
  </v-app>
</template>

<style>
.main-content {
  background-color: #ffffff;
  margin-left: 255px;
}
</style>

<script>
import DashboardComponent from '~/components/DashboardComponent.vue'

export default {
  components: {
    DashboardComponent,
  },
}
</script>
