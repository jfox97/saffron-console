<template>
  <div class="home">
    <div class="wrapper">
      <TransactionView :transactions="transactions" />
    </div>
  </div>
</template>

<script>
import TransactionView from "../components/TransactionView.vue"
export default {
  name: 'Home',
  components: {
    TransactionView
  },
  computed: {
    transactions() {
      return this.$root.$data.transactions;
    }
  }
}
</script>

<style scoped>
.wrapper {
  margin: 40px auto;
  width: 1200px;
}
</style>
