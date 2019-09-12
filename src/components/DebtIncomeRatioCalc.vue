<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col text-center">
          <h5>
            <h1>{{ msg }}</h1>
          </h5>
        </div>
      </div>
      <div class="row">
        <div class="col-8 border">
          <form id="form" v-on:submit="calculate">
            <div class="row">
              <div class="col">
                <div class="row">
                  <div class="col text-center">
                    <h5>
                      <span class="badge badge-secondary">Expense</span>
                    </h5>
                  </div>
                </div>
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
                        v-model.number="expense.monthlyMortgagePayment"
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
                      />
                      <label
                        class="form-check-label"
                        for="gridCheck"
                      >click here to fill out individual items below</label>
                    </div>
                  </div>
                </div>
                <div v-if="expense.checked">
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
                          v-model.number="expense.monthlyPayment"
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
                          v-model.number="expense.annualPropertyTax"
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
                          v-model.number="expense.annualPropertyInsurance"
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
                          v-model.number="expense.annualHoaFees"
                          v-bind:class="{ 'is-invalid': invalidAnnualHoaFees }"
                          :disabled="!expense.checked"
                        />
                        <div class="invalid-feedback">This field is required and must be numeric.</div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="col">
                <div class="row">
                  <div class="col text-center">
                    <h5>
                      <span class="badge badge-secondary">Income</span>
                    </h5>
                  </div>
                </div>
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
                        v-model.number="income.grossIncome"
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
                      />
                      <label
                        class="form-check-label"
                        for="gridCheck"
                      >click here to fill out individual items below</label>
                    </div>
                  </div>
                </div>
                <div v-if="income.checked">
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
                          v-model.number="income.annualSalary"
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
                          v-model.number="income.spouceAnnualSalary"
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
                          v-model.number="income.otherIncome"
                          v-bind:class="{ 'is-invalid': invalidOtherIncome }"
                          :disabled="!income.checked"
                        />
                        <div class="invalid-feedback">This field is required and must be numeric.</div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col">
                <button class="btn btn-primary">Calculate</button>
              </div>
            </div>
          </form>
        </div>
        <div class="col-4">
          <div class="row border border-left-0">
            <div class="col">
              <div class="row">
                <div class="col text-center">
                  <h5>
                    <span class="badge badge-secondary">Result</span>
                  </h5>
                </div>
              </div>
              <div class="row">
                <div class="col">
                  <div class="form-group">
                    <label for="text">Debt to Income Ratio</label>
                    <div class="input-group">
                      <span
                        class="form-control"
                        v-bind:class="{ 'is-invalid': !validForm }"
                      >{{ ratio }}</span>
                      <div class="input-group-append">
                        <span class="input-group-text">%</span>
                      </div>
                      <div class="invalid-feedback">Missing fields</div>
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
        monthlyMortgagePayment: null,
        monthlyPayment: null,
        annualPropertyTax: null,
        annualPropertyInsurance: null,
        annualHoaFees: null,
        checked: false
      },
      income: {
        grossIncome: null,
        annualSalary: null,
        spouceAnnualSalary: null,
        otherIncome: null,
        checked: false
      },
      ratio: null,
      validForm: null
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
    calculate(event) {
      this.validForm = this.isValidForm();
      if (this.validForm) {
        if (this.expense.checked) {
          this.computeMonthlyMortgagePayement();
        }
        if (this.income.checked) {
          this.computeGrossIncome();
        }
        this.ratio = (
          100 *
          (this.expense.monthlyMortgagePayment / this.income.grossIncome)
        ).toFixed(2);
        event.preventDefault();
        console.log("validForm");
      } else {
        event.preventDefault();
        this.ratio = null;
      }
    },
    computeMonthlyMortgagePayement() {
      this.expense.monthlyMortgagePayment = (
        this.expense.monthlyPayment +
        (this.expense.annualPropertyTax +
          this.expense.annualPropertyInsurance +
          this.expense.annualHoaFees) /
          12
      ).toFixed(2);
    },
    computeGrossIncome() {
      this.income.grossIncome = (
        (this.income.annualSalary +
          this.income.spouceAnnualSalary +
          this.income.otherIncome) /
        12
      ).toFixed(2);
    },
    isValidForm() {
      if (!this.expense.checked) {
        if (this.invalidMonthlyMortgagePayment) {
          return false;
        }
      } else if (
        this.invalidMonthlyPayment ||
        this.invalidAnnualPropertyTax ||
        this.invalidAnnualPropertyInsurance ||
        this.invalidAnnualHoaFees
      ) {
        return false;
      }
      if (!this.income.checked) {
        if (this.invalidGrossIncome) {
          return false;
        }
      } else if (
        this.invalidAnnualSalary ||
        this.invalidSpouceAnnualSalary ||
        this.invalidOtherIncome
      ) {
        return false;
      }
      return true;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
