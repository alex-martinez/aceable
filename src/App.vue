<template>
  <div>
    <ProductList/>
  </div>
</template>

<script>
import ProductList from './components/ProductList';

export default {
  name: 'App',
  components: {
    ProductList,
  },
};
</script>

<style lang="scss">
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    "Helvetica Neue", Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
