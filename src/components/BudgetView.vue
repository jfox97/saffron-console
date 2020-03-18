<template>
  <table>
    <thead>
      <th>Category</th>
      <th>Spending</th>
    </thead>
    <tbody>
      <tr v-for="category in categorySpending" :key="category.category">
        <td>{{category.category}}</td>
        <td class="align-right">{{category.spending}}</td>
      </tr>
    </tbody>
</table>
</template>

<script>
export default {
  name: 'BudgetView',
  props: {
    transactions: Array
  },
  computed: {
    categorySpending() {
      let totalSpending = [];
      let allCategories = this.transactions.map(transaction => transaction.category)
      let uniqueCategories = allCategories.filter(function (value, index, self) {
        return self.indexOf(value) === index;
      });
      for (let i = 0; i < uniqueCategories.length; i++) {
        let spending = this.transactions.reduce(function(total, current) {
          if (current.category === uniqueCategories[i]) {
            return total + Number(current.amount.replace(/[^0-9.-]+/g,""));
          }
          return total;
        }, 0);
        let spendingString = "$" + spending.toFixed(2).toString();
        totalSpending.push({
          category: uniqueCategories[i],
          spending: spendingString
        });
      }
      return totalSpending;
    }
  }
}
</script>

<style scoped>
table {
  text-align: left;
  border-collapse: collapse;
  width: 100%;
}

th {
  color: white;
  background-color: #EC4E20;
}

th, td {
  padding: 10px;
  border: 1px solid #ddd;
}

tbody tr:nth-child(even) {
  background-color: #ebeffa;
}

.align-right {
  text-align: right;
}
</style>
