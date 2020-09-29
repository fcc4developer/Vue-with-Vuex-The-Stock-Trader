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
        <a class="nav-link">End Day</a>
      </li>
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Save & Load
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
          <a class="dropdown-item" href="#">Save Data</a>
          <a class="dropdown-item" href="#">Load Data</a>
        </div>
      </li>
    </ul>

  </div>
</nav>
</template>

<script>
  export default {
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    }  }
</script>

<style>
</style>
