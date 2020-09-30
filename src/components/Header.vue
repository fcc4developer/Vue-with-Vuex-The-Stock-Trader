<template>
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <router-link to="/">
    <a class="navbar-brand">Stock Trader</a>
  </router-link>

  <div class="collapse navbar-collapse">
    <ul class="navbar-nav mr-auto">
      <router-link to="/portfolio"  tag="li" class="nav-item" activeClass="active">
        <a class="nav-link">Portfolio</a>
      </router-link>
      <router-link to="/stocks" tag="li" class="nav-item" activeClass="active">
        <a class="nav-link">Stocks</a>
      </router-link>
    </ul>
    <strong class="navbar-text ml-auto">Funds: {{ funds | currency }}</strong>
    <ul class="navbar-nav ml-auto">
      <li class="nav-item">
        <a class="nav-link" @click="endDay">End Day</a>
      </li>
      <li class="nav-item dropdown" @click="isDropdownOpen = !isDropdownOpen">
        <a class="nav-link dropdown-toggle" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Save & Load
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown" :class="{show: isDropdownOpen}">
          <a class="dropdown-item" @click="onSaveData" href="#">Save Data</a>
          <a class="dropdown-item" @click="onLoadData" href="#">Load Data</a>
        </div>
      </li>
    </ul>

  </div>
</nav>
</template>

<script>
  import {mapActions} from 'vuex';

  export default {
    data() {
      return {
        isDropdownOpen: false
      }
    },
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    },
    methods: {
      ...mapActions([
        'randomizeStocks',
        'loadData'
      ]),
      endDay() {
        this.randomizeStocks();
      },
      onSaveData() {
        const data = {
          funds: this.$store.getters.funds,
          stockPortfolio: this.$store.getters.stockPortfolio,
          stocks: this.$store.getters.stocks
        }
        this.$http.put('data.json', data);
      },
      onLoadData() {
        this.loadData();
      }
    }
  }
</script>

<style scoped>
  a {
    cursor: pointer;
  }
</style>
