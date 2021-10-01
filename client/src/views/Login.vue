<template>
  <BasicLayouts>
    <h1>Estamos en Login..</h1>

    <router-link to="/register">
      Crear Cuenta
    </router-link>
  </BasicLayouts>
</template>

<script>
import BasicLayouts from '../layouts/BasicLayouts.vue';
export default {
  name: 'Login',
  components: {
    BasicLayouts,
  },
};
</script>

<style></style>
