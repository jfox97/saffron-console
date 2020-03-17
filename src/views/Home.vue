<template>
  <div class="home">
    <div id="wrapper">
      <h1>Summary for February</h1>
      <h2>Budget</h2>
      <div id="budgetSummary">
        <BudgetView  :transactions="transactions"/>
      </div>
      <h2>Transactions</h2>
      <div id="transactionSummary">
        <TransactionView :transactions="transactions" />
      </div>
    </div>
  </div>
</template>

<script>
import BudgetView from "../components/BudgetView.vue"
import TransactionView from "../components/TransactionView.vue"
export default {
  name: 'Home',
  components: {
    BudgetView,
    TransactionView
  },
  computed: {
    transactions() {
      let firstDayOfMonth = new Date("2020-02-01");
      return this.$root.$data.transactions.filter(function (value) {
        let day = new Date(value.date);
        if (day >= firstDayOfMonth)
          return value;
      });
    }
  }
}
</script>

<style scoped>
#wrapper {
    text-align: left;
    width: 1200px;
    margin: 0px auto;
}

h1 {
  text-align: center;
  margin: 40px 0px 80px 0px;
}

h2, h3 {
  margin-left: 20px;
}

#budgetSummary {
    margin: 40px auto;
    width: 500px;
}

#transactionSummary {
  margin: 40px 0px;
  width: 1200px;
}
</style>
