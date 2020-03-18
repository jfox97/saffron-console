<template>
  <div id="wrapper">
    <h1>Add Transactions</h1>
    <form v-on:submit.prevent="addTransaction">
      <input type="text" placeholder="Description" v-model="description" />
      <input type="text" placeholder="Category" v-model="category" />
      <input type="text" placeholder="Amount" v-model="amount" />
      <button type="submit">Add</button>
    </form>
    <TransactionView :transactions="transactions" />
  </div>
</template>

<script>
import TransactionView from "../components/TransactionView.vue"
import moment from "moment"
export default {
  name: 'Transactions',
  components: {
    TransactionView
  },
  data() {
    return {
      description: "",
      category: "",
      amount: ""
    }
  },
  computed: {
    transactions() {
      return this.$root.$data.transactions;
    }
  },
  methods: {
    addTransaction() {
      if (this.amount === "")
        return;

      if (isNaN(this.amount))
        return;

      let moneyAmount = "$" + Number(this.amount).toFixed(2).toString();
      let date = moment().format("YYYY-MM-DD");
      let lastTransactionIndex = this.$root.$data.transactions.length - 1;
      let lastTransactionID = this.$root.$data.transactions[lastTransactionIndex].id;

      this.$root.$data.transactions.push({
        id: lastTransactionID + 1,
        date: date,
        description: this.description,
        category: this.category,
        amount: moneyAmount
      });

      this.description = "";
      this.category = "";
      this.amount = "";
    }
  }
}
</script>

<style scoped>
  #wrapper {
    width: 1200px;
    margin: 40px auto;
  }

  h1 {
      text-align: left;
  }

  form {
    display: flex;
    justify-content: space-around;
    align-items: center;
    margin: 40px 0px;
  }

  form input {
    padding: 5px 10px;
    width: 300px;
    border: 1px solid #ddd;
    border-radius: 3px;
    font-size: 18px;
  }

  form button {
    font-size: 14px;
    font-weight: 600;
    background-color: #EC4E20;
    color: #f8f9fa;
    border: 0px;
    border-radius: 5px;
    padding: 8px 45px;
  }

  form button:hover {
    cursor: pointer;
    background-color: #e02800;
  }
</style>
