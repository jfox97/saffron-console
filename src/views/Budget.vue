<template>
  <div id="wrapper">
    <h1>Budget</h1>
    <div id="date-filter">
      <label>Budget Period:</label>
      <input type="date" v-model="minDate" /> &mdash;
      <input type="date" v-model="maxDate" />
    </div>
    <BudgetView :transactions="transactions" />
  </div>
</template>

<script>
import BudgetView from "../components/BudgetView.vue"
export default {
  name: 'Budget',
  components: {
    BudgetView
  },
  data() {
    return {
      minDate: "2020-02-01",
      maxDate: "2020-02-29"
    }
  },
  computed: {
    transactions() {
      let minDate = this.minDate
      let maxDate = this.maxDate
      return this.$root.$data.transactions.filter(function(transaction) {
        if (transaction.date >= minDate && transaction.date <= maxDate)
          return transaction;
      });
    }
  }
}
</script>

<style scoped>
  h1 {
      text-align: left;
      margin: 40px 0px;
  }

  #wrapper {
    width: 800px;
    margin: 40px auto;
  }

  #date-filter {
    text-align: left;
    margin: 10px;
  }

  #date-filter input {
    margin: 0px 20px;
    border: 1px solid #ddd;
    border-radius: 3px;
    padding: 2px 5px;
    font-size: 14px;
    font-family: 'Lato', sans-serif;
    color: #484e61;
  }
</style>
