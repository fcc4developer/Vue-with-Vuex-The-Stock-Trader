<template>
  <div class="col-sm-6 col-md-6">
    <div class="card text-white">
        <div class="card-header bg-info">
            <h5 class="card-title pt-2">{{ stock.name }}
              <small class="card-text">(Price: {{ stock.price }})</small>
            </h5>
        </div>
        <div class="card-body">
          <div class="float-left">
              <input
                type="number"
                class="form-control"
                placeholder="Quantity"
                v-model="quantity"
                :class="{danger: insufficientFunds}"
                >
          </div>
          <div class="float-right">
              <button
                class="btn btn-success"
                @click="buyStock"
                :disabled="insufficientFunds || quantity <= 0"
                >{{ insufficientFunds ? 'Not enough founds' : 'Buy'}}</button>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    computed: {
      funds() {
        return this.$store.getters.funds;
      },
      insufficientFunds() {
        return this.quantity * this.stock.price > this.funds;
      }
    },
    methods: {
      buyStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity,
        }
        this.$store.dispatch('buyStock', order);
        this.quantity = 0;
      }
    }
  }
</script>

<style scoped>
  .danger {
    border: 1px red solid;
  }
</style>
