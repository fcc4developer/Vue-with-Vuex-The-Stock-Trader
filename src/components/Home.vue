<template>
  <div class="container">
    <h1>Trade or View your Portfolio</h1>
    <h5>You may Save & Load your Data</h5>
    <h5>Click on 'End Day' to begin a New day!</h5>
    <p>Your Funds: {{ funds | currency}}</p>
  </div>
</template>

<script>
  export default {
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    }
  }
</script>
<style scoped>
  h1 {
    padding: 30px;
  }
  h5, p {
    padding: 10px 30px;
  }
</style>
