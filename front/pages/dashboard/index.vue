<template>
  <div>
    <DashboardComponent />
  </div>
</template>

<script>
export default {
  middleware: 'auth',
  data() {
    return {};
  },
};
</script>

<style scoped>

</style>