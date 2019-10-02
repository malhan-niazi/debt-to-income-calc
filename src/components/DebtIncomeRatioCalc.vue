<template>
  <div class="calculator">
    <div class="container">
      <div class="row">
        <div class="col text-center">
          <h4>{{ msg }}</h4>
        </div>
      </div>
      <nav>
        <div id="nav-tab" class="nav nav-tabs" role="tablist">
          <a
            id="input-tab"
            class="nav-item nav-link"
            data-toggle="tab"
            href="#input-tab-content"
            role="tab"
            aria-controls="input"
            aria-selected="true"
            :class="{ 'active': visibleTab === 0}"
            @click="visibleTab = 0"
          >Input</a>
          <a
            id="result-tab"
            class="nav-item nav-link"
            data-toggle="tab"
            href="#result-tab-content"
            role="tab"
            aria-controls="result"
            aria-selected="false"
            :class="[ratio == null ? 'disabled': '',
                     visibleTab === 1 ? 'active' : '']"
            @click="visibleTab = 1"
          >Result</a>
        </div>
      </nav>
      <div id="tabContent" class="tab-content">
        <div
          id="input-tab-content"
          class="tab-pane fade"
          role="tabpanel"
          aria-labelledby="input-tab"
          :class="{ 'show active': visibleTab === 0 }"
        >
          <InputComponent v-on:submit-form="displayResults"></InputComponent>
        </div>
        <div
          id="result-tab-content"
          class="tab-pane fade"
          role="tabpanel"
          aria-labelledby="result-tab"
          :class="{ 'show active': visibleTab === 1 }"
        >
          <ResultComponent v-bind:result="result"></ResultComponent>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import InputComponent from "./InputComponent.vue";
import ResultComponent from "./ResultComponent.vue";

export default {
  name: "DebtIncomeRatioCalc",
  components: {
    InputComponent,
    ResultComponent
  },
  data() {
    return {
      msg: "Debt-to-Income Calculator",
      result: {
        expense: null,
        income: null,
        ratio: null
      },
      visibleTab: 0
    };
  },
  methods: {
    displayResults(expense, income) {
      this.result.expense = parseFloat(expense);
      this.result.income = parseFloat(income);
      this.result.ratio = this.calculateRatio(
        this.result.expense,
        this.result.income
      );
      this.visibleTab = 1;
    },
    calculateRatio(x, y) {
      return (100 * (parseFloat(x) / parseFloat(y))).toFixed(2);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
