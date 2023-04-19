<template>
<section>
  <div id="app">
    <h1>OD Billing Calculator<span class="highlight">.</span></h1>
    <div class="grid-2">
      <div>
    
    <label>OD Percentage
    <input type="number" placeholder="40" id="percentage" v-model.number="percentage"></label>
    <label>Total $ Collected
    <input type="number" placeholder="4,500" id="total-collected" v-model.number="totalCollected"></label>
    <label>Total $ Paid
    <input type="number" placeholder="2,000" id="total-paid" v-model.number="totalPaid"></label>
    <label>Previous Invoice $ Amount
    <input type="number" placeholder="500" id="total-paid-2" v-model.number="prevInvoiceAmount"></label>
    <!-- <h2>${{ owedAmount }}</h2> -->
</div>
    <div>

    <h4>Invoice Format:</h4>
    <p>Total Collected: {{ totalCollected | toCurrency }}</p>
    <p>{{ percentage }}%: {{ calcPercentage | toCurrency }}</p>
    <p>Total Paid: {{ sumPaid | toCurrency }}</p>
    <p>Total Due: {{ amountDue | toCurrency }}</p>

    <button class="reset-button" onClick="window.location.reload();">Reset</button>

    </div>
    </div>


  </div>
  </section>
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
      return this.totalPaid + this.prevInvoiceAmount
    },
    calcPercentage: function () {
      return this.totalCollected * (this.percentage / 100)
    },
    amountDue: function () {
      return (this.totalCollected * (this.percentage / 100)) - (this.totalPaid + this.prevInvoiceAmount)
    }
  }
}


</script>

<style>
.grid-2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 5%;
}

.highlight {
  font-family: Comfortaa;
  color: #0baaaa;
  font-weight: bold;
  font-size: 120%;
}

.reset-button {
  border: 1px solid #0baaaa;
  color: #0baaaa;
  text-transform: uppercase;
  padding: 10px 20px;
  font-family: Quicksand;
  font-weight: bold;
  background-color: transparent;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 35px;
}

section {
  background-color: rgba(11,170,170, 0.1);
  min-height: 100vh;
  padding-top: 70px;
}

.grid-2 div {
  background-color: white;
  box-shadow: 0px 3px 15px rgba(0,0,0,0.05);
  border-radius: 10px;
  padding: 35px;
}

body {
  margin: 0px;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin: 0 auto;
  max-width: 1080px;
  width: 85%;
  
}

#app h1 {
  font-family: 'Quicksand', sans-serif;
  font-weight: bold;
}

#app label, #app input {
  width: calc(100% - 30px);
  text-align: left;
  font-family: "Avenir";
}

#app input {
  margin-bottom: 25px;
  margin-top: 15px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
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
  color: #0baaaa;
}

@media only screen and (max-width: 1000px){
  .grid-2 {
    grid-template-columns: 1fr;
  }
}

</style>
