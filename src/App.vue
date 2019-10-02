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

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 5%;
}
.background {
  &--gray {
    background-color: #f2f2f2;
  }
  &--rounded {
    border-radius: 5px;
  }
}
.margin {
  &--bottom {
    margin-bottom: 0.25rem;
  }
}
.color {
  &--blue {
    color: #007697;
  }
}
.padding {
  padding: 5px;
  &-label {
    padding: 1rem 1rem 5px 1rem;
  }
  &-p {
    padding: 0px 1rem 0px 1rem;
  }
  &-button {
    padding: 0px 5px 0px 5px;
  }
  &-right {
    padding-right: 15px;
  }
  &-left {
    padding-left: 4rem;
    &--none {
      padding-left: 0px;
    }
  }
}
</style>
