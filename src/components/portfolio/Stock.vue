<template>
  <div class="col-sm-6 col-md-4">
    <div class="card text-white">
        <div class="card-header bg-info">
            <h5 class="card-title pt-2">{{ stock.name }}
                <small class="card-text">
                  (Price: {{ stock.price }} Quantity: {{ stock.quantity }})
                </small>
            </h5>
        </div>
        <div class="card-body">
            <div class="float-left">
                <input
                  type="number"
                  class="form-control"
                  placeholder="Quantity"
                  v-model="quantity"
                  >
            </div>
            <div class="float-right">
                <button
                  class="btn btn-success"
                  @click="sellStock"
                  :disabled="quantity <= 0"
                  >Sell</button>
            </div>
          </div>
      </div>
  </div>
</template>

<script>
  import { mapActions } from 'vuex';

  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    methods: {
      ...mapActions({
        placeSellOrder: 'sellStock'
      }),
      sellStock() {
        const order = {
          stockId: this.stock.id,
          stockprice: this.stock.price,
          quantity: this.quantity,
        };
        this.placeSellOrder(order);
        this.quantity = 0;
      }
    }
  }
</script>

<style scoped>
</style>
