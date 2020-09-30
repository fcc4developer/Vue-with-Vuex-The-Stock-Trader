<template>
  <div class="container">
    <template v-if="stocks.length > 0">
      <div class="row">
        <app-stock v-for="stock in stocks" :key="stock.id" :stock="stock"></app-stock>
      </div>
    </template>
    <template v-else>
      <div class="row">
        <h2>Currently your Stocks Portfolio is empty</h2>
      </div>
    </template>
  </div>
</template>

<script>
  import Stock from './Stock';

  export default {
    components: {
      appStock: Stock
    },
    computed: {
      stocks() {
        return this.$store.getters.stockPortfolio;
      }
    }
  }
</script>

<style scoped>
  .row {
    padding: 30px;
  }
  h2 {
    color: gray;
    padding: 0 30px;
  }
</style>
