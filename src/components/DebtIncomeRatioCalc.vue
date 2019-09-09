<template>
  <div>
    <h1>{{ msg }}</h1>
    <div class="container">
      <div class="row">
        <div class="col-8 border">
          <div class="row">
            <div class="col">
              <h5>
                <span class="badge badge-secondary">Expense</span>
              </h5>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Total First Mortgage Monthly Payment(s)</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="expense.monthlyMortgagePayment"
                      v-bind:class="{ 'is-invalid': invalidMonthlyMortgagePayment }"
                      :disabled="expense.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <div class="form-check">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="expenseInfoChecked"
                      v-model="expense.checked"
                      @change="resetExpense()"
                    />
                    <label
                      class="form-check-label"
                      for="gridCheck"
                    >click here to fill out individual items below</label>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Monthly Payment</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="expense.monthlyPayment"
                      v-bind:class="{ 'is-invalid': invalidMonthlyPayment }"
                      :disabled="!expense.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Annual Property Taxes</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="expense.annualPropertyTax"
                      v-bind:class="{ 'is-invalid': invalidAnnualPropertyTax }"
                      :disabled="!expense.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Annual Property Insurance</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="expense.annualPropertyInsurance"
                      v-bind:class="{ 'is-invalid': invalidAnnualPropertyInsurance }"
                      :disabled="!expense.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Annual HOA Fees</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="expense.annualHoaFees"
                      v-bind:class="{ 'is-invalid': invalidAnnualHoaFees }"
                      :disabled="!expense.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="col">
              <h5>
                <span class="badge badge-secondary">Income</span>
              </h5>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Gross Monthly Income</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="income.grossIncome"
                      v-bind:class="{ 'is-invalid': invalidGrossIncome }"
                      :disabled="income.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <div class="form-check">
                    <input
                      class="form-check-input"
                      type="checkbox"
                      id="incomeInfoChecked"
                      v-model="income.checked"
                      @change="resetIncome()"
                    />
                    <label
                      class="form-check-label"
                      for="gridCheck"
                    >click here to fill out individual items below</label>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Annual Salary</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="income.annualSalary"
                      v-bind:class="{ 'is-invalid': invalidAnnualSalary }"
                      :disabled="!income.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Spouce or Partners Annual Salary</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="income.spouceAnnualSalary"
                      v-bind:class="{ 'is-invalid': invalidSpouceAnnualSalary }"
                      :disabled="!income.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Other Annual Income</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control"
                      placeholder="enter amount"
                      v-model="income.otherIncome"
                      v-bind:class="{ 'is-invalid': invalidOtherIncome }"
                      :disabled="!income.checked"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <form></form>
        </div>
        <div class="col-4">
          <div class="row border border-left-0">
            <div class="col">
              <div class="row">
                <div class="col">
                  <h5>
                    <span class="badge badge-secondary">Result</span>
                  </h5>
                </div>
              </div>
              <div class="row">
                <div class="col text-center">
                  <div class="form-group">
                    <label for="text">Debt to Income Ratio</label>
                    <div class="input-group">
                      <span class="form-control">{{ ratio }}</span>
                      <div class="input-group-append">
                        <span class="input-group-text">%</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DebtIncomeRatioCalc",
  props: {
    msg: String
  },
  data() {
    return {
      expense: {
        monthlyMortgagePayment: 0,
        monthlyPayment: 0,
        annualPropertyTax: 0,
        annualPropertyInsurance: 0,
        annualHoaFees: 0,
        checked: false
      },
      income: {
        grossIncome: 0,
        annualSalary: 0,
        spouceAnnualSalary: 0,
        otherIncome: 0,
        checked: false
      },
      ratio: 0
    };
  },
  computed: {
    invalidMonthlyMortgagePayment() {
      return this.isInvalid(this.expense.monthlyMortgagePayment);
    },
    invalidMonthlyPayment() {
      return this.isInvalid(this.expense.monthlyPayment);
    },
    invalidAnnualPropertyTax() {
      return this.isInvalid(this.expense.annualPropertyTax);
    },
    invalidAnnualPropertyInsurance() {
      return this.isInvalid(this.expense.annualPropertyInsurance);
    },
    invalidAnnualHoaFees() {
      return this.isInvalid(this.expense.annualHoaFees);
    },
    invalidGrossIncome() {
      return this.isInvalid(this.income.grossIncome);
    },
    invalidAnnualSalary() {
      return this.isInvalid(this.income.annualSalary);
    },
    invalidSpouceAnnualSalary() {
      return this.isInvalid(this.income.spouceAnnualSalary);
    },
    invalidOtherIncome() {
      return this.isInvalid(this.income.otherIncome);
    }
  },
  methods: {
    isInvalid(n) {
      return this.isEmpty(n) || !this.isNumeric(n);
    },
    isEmpty(n) {
      return n === "";
    },
    isNumeric(n) {
      return !isNaN(parseFloat(n)) && isFinite(n);
    },
    resetIncome() {},
    resetExpense() {}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
