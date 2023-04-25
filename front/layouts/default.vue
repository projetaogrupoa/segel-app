<template>
  <v-app class="body" :light="$vuetify.theme.light" style="background: var(--v-primary-base)">
    <v-main>
      <Nuxt />
    </v-main>
  </v-app>
</template>


<style scoped>
.body {
  overflow: hidden;
  height: 100vh;
}
</style>