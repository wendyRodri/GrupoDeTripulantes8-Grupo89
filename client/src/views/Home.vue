<template>
  <BasicLayouts>
    <h1>Estamos en Home</h1>
  </BasicLayouts>
</template>

<script>
import { ref, onMounted } from 'vue';
import BasicLayouts from '../layouts/BasicLayouts.vue';
import { getProducts } from '../api/pruduct';
export default {
  name: 'Home',
  components: {
    BasicLayouts,
  },
  setup() {
    let products = ref(null);

    onMounted(async () => {
      const response = await getProducts(1);
      products.value = response;
    });
    return {
      products,
    };
  },
};
</script>
