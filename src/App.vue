<template>
  <div id="app">
    <DebtIncomeRatioCalc msg="Debt-to-Income Calculator" />
  </div>
</template>

<script>
import DebtIncomeRatioCalc from "./components/DebtIncomeRatioCalc.vue";

export default {
  name: "app",
  components: {
    DebtIncomeRatioCalc
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 5%;
}
</style>
