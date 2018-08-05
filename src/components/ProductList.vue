<template>
  <div class="py-4 bg-light">
    <div class="container">
      <div class="row">
        <div
          v-if="products.length"
          v-for="product in products"
          v-bind:key="product.id"
          class="col-sm-6 col-lg-4 col-xl-3 py-3">
          <ProductCard
            v-bind="product" />
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import axios from 'axios';
import ProductCard from './ProductCard';

const REQUEST_URL = 'https://mkt-endpoint.now.sh/products';

export default {
  name: 'ProductList',

  components: {
    ProductCard,
  },

  data() {
    return {
      products: [],
    };
  },

  methods: {
    /**
     * Sorts products by price in either ascending or descending order.
     * @param  {Array}   products    List of objects
     * @param  {Boolean} isAscending
     * @return {Array}
     */
    sortByPrice(products = [], isAscending = true) {
      return products.slice().sort((a, b) => (isAscending ? a.price - b.price : b.price - a.price));
    },
  },

  beforeMount() {
    axios.get(REQUEST_URL)
      .then(({ data }) => {
        this.products = this.sortByPrice(data);
      });
  },
};
</script>
