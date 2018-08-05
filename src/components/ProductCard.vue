<template>
  <div class="card">
    <div class="card-body">
      <h4 class="card-title">{{ title }}</h4>
      <p class="card-text">{{ description }}</p>
      <div class="text-primary">${{ formatPrice( price ) }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    description: {
      required: true,
      type: String,
    },

    price: {
      required: true,
      type: Number,
    },

    title: {
      required: true,
      type: String,
    },

    state: {
      required: true,
      type: String,
    },
  },

  methods: {
    /**
     * Takes the price of an item, adds cents values, and adds commas in correct placement if needed.
     * @param  {Number} price Price to be formatted
     * @return {String}
     */
    formatPrice(price) {
      return this.numberWithCommas(price.toFixed(2));
    },

    /**
     * Formats numbers with commas denoting thousands, millions, billions, etc.
     * 10      => 10
     * 1200    => 1,200
     * 1234567 => 1,234,567
     * @reference
     * http://stackoverflow.com/questions/2901102/how-to-print-a-number-with-commas-as-thousands-separators-in-javascript
     * @param  {Number} num Number without commas
     * @return {String}
     */
    numberWithCommas(num) {
      return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    },
  },
};
</script>
