<template>
  <div id="app">
    <h1>OD Billing Calculator</h1>
    <label>OD percentage
    <input type="number" placeholder="40" id="percentage" v-model.number="percentage"></label>
    <label>Total $ Collected
    <input type="number" placeholder="4,500" id="total-collected" v-model.number="totalCollected"></label>
    <label>Total Paid
    <input type="number" placeholder="2,000" id="total-paid" v-model.number="totalPaid"></label>
    <label>Previous Invoice Amount
    <input type="number" placeholder="500" id="total-paid-2" v-model.number="prevInvoiceAmount"></label>
    <!-- <h2>${{ owedAmount }}</h2> -->

    <hr>

    <h4>Invoice Format:</h4>
    <p>Total Collected: ${{ totalCollected }}</p>
    <p>{{ percentage }}%: ${{ calcPercentage }}</p>
    <p>Total Paid: ${{ sumPaid }}</p>
    <p>Total Due: ${{ amountDue }}</p>


  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      totalCollected: 0,
      percentage: 0,
      totalPaid: 0,
      prevInvoiceAmount: 0
    }
  },
  computed: {
    // owedAmount: function () {
    //   return this.percentage + this.totalCollected
    // },
    sumPaid: function () {
      // return this.totalPaid + this.prevInvoiceAmount
      return parseFloat(this.totalPaid + this.prevInvoiceAmount).toFixed(2)
    },
    calcPercentage: function () {
      return (this.totalCollected).toFixed(2) * (this.percentage / 100)
    },
    amountDue: function () {
      return ((this.totalCollected).toFixed(2) * (this.percentage / 100)) - (parseFloat(this.totalPaid + this.prevInvoiceAmount).toFixed(2))
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
