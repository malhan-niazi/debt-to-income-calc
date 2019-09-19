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
        <div class="col">
          <div class="row">
            <div class="col">
              <div class="row padding-label">
                <h5>
                  <span class>How to Use</span>
                </h5>
              </div>
              <div class="row padding-p background--gray">
                <p>This Debt-to-Income Ratio calculator is provided to help you determine the percentage of how much you pay each month for your mortgage(s) compared to your total monthly gross income.</p>
                <p>This calculator returns information based on your inputs regarding your existing mortgage information. It is important that you provide accurate information in order to receive more realistic results.</p>
              </div>
            </div>
          </div>
          <form action>
            <div class="row">
              <div class="col">
                <div class="row padding-label color-blue font-weight-bold">
                  <h5>
                    <span class>Your Existing Mortgage Information</span>
                  </h5>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray padding margin-bottom">
              <label
                for="expense1"
                class="col-sm-6 padding-right-none col-form-label font-weight-bold"
              >Total First Mortgage Monthly Payment(s)</label>
              <div class="col-sm-6 padding-right-none">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    type="text"
                    class="form-control rounded-right"
                    id="expense1"
                    placeholder="Mortgage Monthly Payment(s)"
                    v-model="expense.monthlyMortgagePayment.value"
                    v-bind:class="{ 'is-invalid': !expense.monthlyMortgagePayment.isValid }"
                    @input="validateMonthlyMortgagePayment"
                    :disabled="expense.checked"
                  />
                  <div class="invalid-feedback">This field is required and must be numeric.</div>
                </div>
              </div>
            </div>
            <div class="row padding-p background--gray margin-bottom">
              <p>This should include your first monthly mortgage payment, as well as any additional mortgage payments you may have. It should also include principal, interest, taxes, insurance and homeowner's association fees. If you have an escrow account set up on your first mortgage, these costs will be included in your monthly payment.</p>
            </div>
            <div class="form-group row background--gray padding margin-bottom">
              <div class="col-sm-10">
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    id="expenseRadio1"
                    v-model="expense.checked"
                    v-bind:value="false"
                    checked
                  />
                  <label
                    class="form-check-label"
                    for="expenseRadio1"
                  >Fill out consolidated Mortgage Monthly Payment(s) above.</label>
                </div>
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    id="expenseRadio2"
                    v-model="expense.checked"
                    v-bind:value="true"
                  />
                  <label
                    class="form-check-label"
                    for="expenseRadio1"
                  >If not, click here and fill in the information below.</label>
                </div>
              </div>
            </div>
            <div v-if="expense.checked">
              <div class="form-group row background--gray padding margin-bottom">
                <label
                  for="expense2"
                  class="col-sm-6 padding-right-none col-form-label padding-left font-weight-bold"
                >Monthly Payment</label>
                <div class="col-sm-6 padding-right-none">
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control rounded-right"
                      id="expense2"
                      placeholder="Monthly Payment"
                      v-model="expense.monthlyPayment.value"
                      v-bind:class="{ 'is-invalid': !expense.monthlyPayment.isValid }"
                      @input="validateMonthlyPayment"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="form-group row background--gray padding margin-bottom">
                <label
                  for="expense3"
                  class="col-sm-6 padding-right-none col-form-label padding-left font-weight-bold"
                >Annual Property Taxes</label>
                <div class="col-sm-6 padding-right-none">
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control rounded-right"
                      id="expense3"
                      placeholder="Annual Property Taxes"
                      v-model="expense.annualPropertyTax.value"
                      v-bind:class="{ 'is-invalid': !expense.annualPropertyTax.isValid }"
                      @input="validateAnnualPropertyTax"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="form-group row background--gray padding margin-bottom">
                <label
                  for="expense4"
                  class="col-sm-6 padding-right-none col-form-label padding-left font-weight-bold"
                >Annual Property Insurance</label>
                <div class="col-sm-6 padding-right-none">
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control rounded-right"
                      id="expense4"
                      placeholder="Annual Property Insurance"
                      v-model="expense.annualPropertyInsurance.value"
                      v-bind:class="{ 'is-invalid': !expense.annualPropertyInsurance.isValid }"
                      @input="validateAnnualPropertyInsurance"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="form-group row background--gray padding margin-bottom">
                <label
                  for="expense5"
                  class="col-sm-6 padding-right-none col-form-label padding-left font-weight-bold"
                >Annual Home Owner's Association Fees</label>
                <div class="col-sm-6 padding-right-none">
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control rounded-right"
                      id="expense5"
                      placeholder="Annual HOA Fees"
                      v-model="expense.annualHoaFees.value"
                      v-bind:class="{ 'is-invalid': !expense.annualHoaFees.isValid }"
                      @input="validateAnnualHoaFees"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col">
                <div class="row padding-label color-blue font-weight-bold">
                  <h5>
                    <span class>Your Income Information</span>
                  </h5>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray padding margin-bottom">
              <label
                for="income1"
                class="col-sm-6 padding-right-none col-form-label font-weight-bold"
              >Gross Monthly Income</label>
              <div class="col-sm-6 padding-right-none">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    type="text"
                    class="form-control rounded-right"
                    id="income1"
                    placeholder="Monthly Income"
                    v-model="income.grossIncome.value"
                    v-bind:class="{ 'is-invalid': !income.grossIncome.isValid }"
                    @input="validateGrossIncome"
                    :disabled="income.checked"
                  />
                  <div class="invalid-feedback">This field is required and must be numeric.</div>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray padding margin-bottom">
              <div class="col-sm-10">
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    id="incomeRadio1"
                    v-model="income.checked"
                    v-bind:value="false"
                    checked
                  />
                  <label
                    class="form-check-label"
                    for="incomeRadio1"
                  >Fill out consolidated Gross Monthly Income above.</label>
                </div>
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="radio"
                    id="incomeRadio2"
                    v-model="income.checked"
                    v-bind:value="true"
                  />
                  <label
                    class="form-check-label"
                    for="incomeRadio2"
                  >If you are unsure of this amount, click here and fill in the information below.</label>
                </div>
              </div>
            </div>
            <div v-if="income.checked">
              <div class="form-group row background--gray padding margin-bottom">
                <label
                  for="income2"
                  class="col-sm-6 padding-right-none col-form-label padding-left font-weight-bold"
                >Annual Salary</label>
                <div class="col-sm-6 padding-right-none">
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control rounded-right"
                      id="income2"
                      placeholder="Annual Salary"
                      v-model="income.annualSalary.value"
                      v-bind:class="{ 'is-invalid': !income.annualSalary.isValid }"
                      @input="validateAnnualSalary"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="form-group row background--gray padding margin-bottom">
                <label
                  for="income3"
                  class="col-sm-6 padding-right-none col-form-label padding-left font-weight-bold"
                >Spouse or Partner's Annual Salary</label>
                <div class="col-sm-6 padding-right-none">
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control rounded-right"
                      id="income3"
                      placeholder="Partner's Annual Salary"
                      v-model="income.spouceAnnualSalary.value"
                      v-bind:class="{ 'is-invalid': !income.spouceAnnualSalary.isValid }"
                      @input="validateSpouceAnnualSalary"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
              <div class="form-group row background--gray padding margin-bottom">
                <label
                  for="income4"
                  class="col-sm-6 padding-right-none col-form-label padding-left font-weight-bold"
                >Other Annual Income</label>
                <div class="col-sm-6 padding-right-none">
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input
                      type="text"
                      class="form-control rounded-right"
                      id="income4"
                      placeholder="Other Annual Income"
                      v-model="income.otherIncome.value"
                      v-bind:class="{ 'is-invalid': !income.otherIncome.isValid }"
                      @input="validateOtherIncome"
                    />
                    <div class="invalid-feedback">This field is required and must be numeric.</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="form-group row">
              <div class="col">
                <div class="row">
                  <button class="btn btn-primary font-weight-bold">Calculate</button>
                </div>
              </div>
            </div>
          </form>
          <div class="row">
            <div class="col">
              <div class="row padding-label color-blue">
                <h5>
                  <span class>Result</span>
                </h5>
              </div>
            </div>
          </div>
          <div class="form-group row background--gray padding margin-bottom">
            <label
              for="income4"
              class="col-sm-6 padding-right-none col-form-label font-weight-bold"
            >Debt to Income Ratio</label>
            <div class="col-sm-6 padding-right-none">
              <div class="input-group">
                <span class="form-control" v-bind:class="{ 'is-invalid': !validForm }">{{ ratio }}</span>
                <div class="input-group-append">
                  <span class="input-group-text rounded-right">%</span>
                </div>
                <div class="invalid-feedback">{{errMsg}}</div>
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
        monthlyMortgagePayment: {
          value: null,
          isValid: true
        },
        monthlyPayment: {
          value: null,
          isValid: true
        },
        annualPropertyTax: {
          value: null,
          isValid: true
        },
        annualPropertyInsurance: {
          value: null,
          isValid: true
        },
        annualHoaFees: {
          value: null,
          isValid: true
        },
        checked: false
      },
      income: {
        grossIncome: {
          value: null,
          isValid: true
        },
        annualSalary: {
          value: null,
          isValid: true
        },
        spouceAnnualSalary: {
          value: null,
          isValid: true
        },
        otherIncome: {
          value: null,
          isValid: true
        },
        checked: false
      },
      ratio: null,
      validForm: true,
      errMsg: String
    };
  },
  methods: {
    validateMonthlyMortgagePayment() {
      this.expense.monthlyMortgagePayment.isValid = this.isValid(
        this.expense.monthlyMortgagePayment.value
      );
    },
    validateMonthlyPayment() {
      this.expense.monthlyPayment.isValid = this.isValid(
        this.expense.monthlyPayment.value
      );
    },
    validateAnnualPropertyTax() {
      this.expense.annualPropertyTax.isValid = this.isValid(
        this.expense.annualPropertyTax.value
      );
    },
    validateAnnualPropertyInsurance() {
      this.expense.annualPropertyInsurance.isValid = this.isValid(
        this.expense.annualPropertyInsurance.value
      );
    },
    validateAnnualHoaFees() {
      this.expense.annualHoaFees.isValid = this.isValid(
        this.expense.annualHoaFees.value
      );
    },
    validateGrossIncome() {
      this.income.grossIncome.isValid = this.isValid(
        this.income.grossIncome.value
      );
    },
    validateAnnualSalary() {
      this.income.annualSalary.isValid = this.isValid(
        this.income.annualSalary.value
      );
    },
    validateSpouceAnnualSalary() {
      this.income.spouceAnnualSalary.isValid = this.isValid(
        this.income.spouceAnnualSalary.value
      );
    },
    validateOtherIncome() {
      this.income.otherIncome.isValid = this.isValid(
        this.income.otherIncome.value
      );
    },
    isValid(n) {
      return !this.isEmpty(n) && this.isNumeric(n);
    },
    isEmpty(n) {
      return n === "";
    },
    isNumeric(n) {
      return !isNaN(parseFloat(n)) && isFinite(n);
    },
    computeMonthlyMortgagePayement() {
      this.expense.monthlyMortgagePayment.value = (
        this.expense.monthlyPayment.value +
        (this.expense.annualPropertyTax.value +
          this.expense.annualPropertyInsurance.value +
          this.expense.annualHoaFees.value) /
          12
      ).toFixed(2);
    },
    computeGrossIncome() {
      this.income.grossIncome.value = (
        (this.income.annualSalary.value +
          this.income.spouceAnnualSalary.value +
          this.income.otherIncome.value) /
        12
      ).toFixed(2);
    },
    isValidForm() {}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.background--gray {
  background-color: #f2f2f2;
  border-radius: 5px;
}
.margin-bottom {
  margin-bottom: 0.25rem;
}
.color-blue {
  color: lightseagreen;
}
.padding {
  padding: 5px;
}
.padding-label {
  padding: 1rem 5px 0px 1rem;
}
.padding-p {
  padding: 0px 1rem 0px 1rem;
}
.padding-button {
  padding: 0px 5px 0px 5px;
}
.padding-right-none {
  padding-right: 15px;
}
.padding-left {
  padding-left: 4rem;
}
</style>
