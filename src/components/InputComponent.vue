<template>
  <div>
    <div class="row">
      <div class="col">
        <div class="row">
          <div class="col">
            <div class="row padding-label padding-left--none">
              <h4>How to Use</h4>
            </div>
            <div class="row">
              <p>This Debt-to-Income Ratio calculator is provided to help you determine the percentage of how much you pay each month for your mortgage(s) compared to your total monthly gross income.</p>
              <p>This calculator returns information based on your inputs regarding your existing mortgage information. It is important that you provide accurate information in order to receive more realistic results.</p>
            </div>
          </div>
        </div>
        <form id="form" @submit="submitForm">
          <div class="row">
            <div class="col">
              <div
                class="row padding-label background--gray background--rounded color--blue margin--bottom"
              >
                <h4>Your Existing Mortgage Information</h4>
              </div>
            </div>
          </div>
          <div class="form-group row background--gray background--rounded margin--bottom">
            <label
              for="expense1"
              class="col-sm-6 padding-right col-form-label font-weight-bold"
            >Total First Mortgage Monthly Payment(s)</label>
            <div class="col-sm-6 padding-right">
              <div class="input-group">
                <div class="input-group-prepend">
                  <span class="input-group-text">$</span>
                </div>
                <input
                  id="expense1"
                  v-model="expense.monthlyMortgagePayment.value"
                  type="text"
                  class="form-control rounded-right"
                  placeholder="Enter amount"
                  :class="{ 'is-invalid': !expense.monthlyMortgagePayment.isValid }"
                  :disabled="expense.checked"
                  @input="validate(expense.monthlyMortgagePayment)"
                />
                <div class="invalid-feedback">This field is required and must be numeric.</div>
              </div>
            </div>
            <p
              class="padding-p"
            >This should include your first monthly mortgage payment, as well as any additional mortgage payments you may have. It should also include principal, interest, taxes, insurance and homeowner's association fees. If you have an escrow account set up on your first mortgage, these costs will be included in your monthly payment.</p>
          </div>
          <div class="form-group row background--gray background--rounded padding margin--bottom">
            <div class="col-sm-10">
              <div class="form-check">
                <input
                  id="expenseRadio1"
                  v-model="expense.checked"
                  class="form-check-input"
                  type="radio"
                  :value="false"
                  checked
                />
                <label
                  class="form-check-label"
                  for="expenseRadio1"
                >Fill out consolidated Mortgage Monthly Payment(s) above.</label>
              </div>
              <div class="form-check">
                <input
                  id="expenseRadio2"
                  v-model="expense.checked"
                  class="form-check-input"
                  type="radio"
                  :value="true"
                />
                <label
                  class="form-check-label"
                  for="expenseRadio1"
                >If not, click here and fill in the information below.</label>
              </div>
            </div>
          </div>
          <div v-if="expense.checked">
            <div class="form-group row background--gray background--rounded margin--bottom">
              <label
                for="expense2"
                class="col-sm-6 padding-right col-form-label padding-left font-weight-bold"
              >Monthly Payment</label>
              <div class="col-sm-6 padding-right">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    id="expense2"
                    v-model.number="expense.monthlyPayment.value"
                    type="text"
                    class="form-control rounded-right"
                    placeholder="Enter amount"
                    :class="{ 'is-invalid': !expense.monthlyPayment.isValid }"
                    @input="validate(expense.monthlyPayment)"
                  />
                  <div class="invalid-feedback">This field is required and must be numeric.</div>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray background--rounded margin--bottom">
              <label
                for="expense3"
                class="col-sm-6 padding-right col-form-label padding-left font-weight-bold"
              >Annual Property Taxes</label>
              <div class="col-sm-6 padding-right">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    id="expense3"
                    v-model="expense.annualPropertyTax.value"
                    type="text"
                    class="form-control rounded-right"
                    placeholder="Enter amount"
                    :class="{ 'is-invalid': !expense.annualPropertyTax.isValid }"
                    @input="validate(expense.annualPropertyTax)"
                  />
                  <div class="invalid-feedback">This field is required and must be numeric.</div>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray background--rounded margin--bottom">
              <label
                for="expense4"
                class="col-sm-6 padding-right col-form-label padding-left font-weight-bold"
              >Annual Property Insurance</label>
              <div class="col-sm-6 padding-right">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    id="expense4"
                    v-model="expense.annualPropertyInsurance.value"
                    type="text"
                    class="form-control rounded-right"
                    placeholder="Enter amount"
                    :class="{ 'is-invalid': !expense.annualPropertyInsurance.isValid }"
                    @input="validate(expense.annualPropertyInsurance)"
                  />
                  <div class="invalid-feedback">This field is required and must be numeric.</div>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray background--rounded margin--bottom">
              <label
                for="expense5"
                class="col-sm-6 padding-right col-form-label padding-left font-weight-bold"
              >Annual Home Owner's Association Fees</label>
              <div class="col-sm-6 padding-right">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    id="expense5"
                    v-model="expense.annualHoaFees.value"
                    type="text"
                    class="form-control rounded-right"
                    placeholder="Enter amount (optional)"
                    :class="{ 'is-invalid': !expense.annualHoaFees.isValid }"
                    @input="validateOptionalField(expense.annualHoaFees)"
                  />
                  <div class="invalid-feedback">This field must be numeric.</div>
                </div>
              </div>
            </div>
          </div>
          <div class="row">
            <div class="col">
              <div
                class="row padding-label background--gray background--rounded color--blue margin--bottom"
              >
                <h4>Your Income Information</h4>
              </div>
            </div>
          </div>
          <div class="form-group row background--gray background--rounded margin--bottom">
            <label
              for="income1"
              class="col-sm-6 padding-right col-form-label font-weight-bold"
            >Gross Monthly Income</label>
            <div class="col-sm-6 padding-right">
              <div class="input-group">
                <div class="input-group-prepend">
                  <span class="input-group-text">$</span>
                </div>
                <input
                  id="income1"
                  v-model="income.grossIncome.value"
                  type="text"
                  class="form-control rounded-right"
                  placeholder="Enter amount"
                  :class="{ 'is-invalid': !income.grossIncome.isValid }"
                  :disabled="income.checked"
                  @input="validateGreaterThanZero(income.grossIncome)"
                />
                <div
                  class="invalid-feedback"
                >This field is required, must be numeric, and greater than 0</div>
              </div>
            </div>
          </div>
          <div class="form-group row background--gray background--rounded margin--bottom">
            <div class="col-sm-10">
              <div class="form-check">
                <input
                  id="incomeRadio1"
                  v-model="income.checked"
                  class="form-check-input"
                  type="radio"
                  :value="false"
                  checked
                />
                <label
                  class="form-check-label"
                  for="incomeRadio1"
                >Fill out consolidated Gross Monthly Income above.</label>
              </div>
              <div class="form-check">
                <input
                  id="incomeRadio2"
                  v-model="income.checked"
                  class="form-check-input"
                  type="radio"
                  :value="true"
                />
                <label
                  class="form-check-label"
                  for="incomeRadio2"
                >If you are unsure of this amount, click here and fill in the information below.</label>
              </div>
            </div>
          </div>
          <div v-if="income.checked">
            <div class="form-group row background--gray background--rounded margin--bottom">
              <label
                for="income2"
                class="col-sm-6 padding-right col-form-label padding-left font-weight-bold"
              >Annual Salary</label>
              <div class="col-sm-6 padding-right">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    id="income2"
                    v-model="income.annualSalary.value"
                    type="text"
                    class="form-control rounded-right"
                    placeholder="Enter amount"
                    :class="{ 'is-invalid': !income.annualSalary.isValid }"
                    @input="validate(income.annualSalary)"
                  />
                  <div class="invalid-feedback">This field is required and must be numeric.</div>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray background--rounded margin--bottom">
              <label
                for="income3"
                class="col-sm-6 padding-right col-form-label padding-left font-weight-bold"
              >Spouse or Partner's Annual Salary</label>
              <div class="col-sm-6 padding-right">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    id="income3"
                    v-model="income.spouceAnnualSalary.value"
                    type="text"
                    class="form-control rounded-right"
                    placeholder="Enter amount"
                    :class="{ 'is-invalid': !income.spouceAnnualSalary.isValid }"
                    @input="validate(income.spouceAnnualSalary)"
                  />
                  <div class="invalid-feedback">This field is required and must be numeric.</div>
                </div>
              </div>
            </div>
            <div class="form-group row background--gray background--rounded margin--bottom">
              <label
                for="income4"
                class="col-sm-6 padding-right col-form-label padding-left font-weight-bold"
              >Other Annual Income</label>
              <div class="col-sm-6 padding-right">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text">$</span>
                  </div>
                  <input
                    id="income4"
                    v-model="income.otherIncome.value"
                    type="text"
                    class="form-control rounded-right"
                    placeholder="Enter amount"
                    :class="{ 'is-invalid': !income.otherIncome.isValid }"
                    @input="validate(income.otherIncome)"
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
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "InputComponent",
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
      }
    };
  },
  methods: {
    validate(input) {
      input.isValid = this.isValid(input.value);
    },
    validateOptionalField(input) {
      if (this.isFieldOptional(input.value)) {
        input.isValid = true;
      } else {
        input.isValid = this.isNumeric(input.value);
      }
    },
    validateGreaterThanZero(input) {
      input.isValid = this.isValid(input.value) && parseFloat(input.value) > 0;
    },
    isFieldOptional(n) {
      return n == null || this.isEmpty(n);
    },
    isValid(n) {
      // replace with regex
      return !this.isEmpty(n) && this.isNumeric(n);
    },
    isEmpty(n) {
      return n === "";
    },
    isNumeric(n) {
      // eslint-disable-next-line no-restricted-globals
      return !isNaN(parseFloat(n)) && isFinite(n);
    },
    submitForm(event) {
      if (!this.isValidForm(this.expense, this.income)) {
        event.preventDefault();
        return;
      }
      if (this.expense.checked) {
        this.computeMonthlyMortgagePayement();
      }
      if (this.income.checked) {
        this.computeGrossIncome();
      }
      this.$emit(
        "submit-form",
        this.expense.monthlyMortgagePayment.value,
        this.income.grossIncome.value
      );
      event.preventDefault();
    },
    calcMonthlyFromAnnual(nums) {
      let sum = 0;
      nums.forEach(n => {
        sum += parseFloat(n);
      });
      return sum / 12;
    },
    computeMonthlyMortgagePayement() {
      if (this.isFieldOptional(this.expense.annualHoaFees.value)) {
        this.expense.annualHoaFees.value = 0;
      }
      this.expense.monthlyMortgagePayment.value = (
        parseFloat(this.expense.monthlyPayment.value) +
        parseFloat(
          this.calcMonthlyFromAnnual([
            this.expense.annualPropertyTax.value,
            this.expense.annualPropertyInsurance.value,
            this.expense.annualHoaFees.value
          ])
        )
      ).toFixed(2);
    },
    computeGrossIncome() {
      this.income.grossIncome.value = this.calcMonthlyFromAnnual([
        this.income.annualSalary.value,
        this.income.spouceAnnualSalary.value,
        this.income.otherIncome.value
      ]).toFixed(2);
    },
    isValidForm(expense, income) {
      let isIncomeValid = true;
      let isExpenseValid = true;
      if (expense.checked) {
        this.validate(expense.monthlyPayment);
        this.validate(expense.annualPropertyTax);
        this.validate(expense.annualPropertyInsurance);
        this.validateOptionalField(expense.annualHoaFees);
        isExpenseValid =
          expense.monthlyPayment.isValid &&
          expense.annualPropertyTax.isValid &&
          expense.annualPropertyInsurance.isValid &&
          expense.annualHoaFees.isValid;
        expense.monthlyMortgagePayment.isValid = true;
      } else {
        this.validate(expense.monthlyMortgagePayment);
        isExpenseValid = expense.monthlyMortgagePayment.isValid;
      }
      if (income.checked) {
        this.validate(income.annualSalary);
        this.validate(income.spouceAnnualSalary);
        this.validate(income.otherIncome);
        isIncomeValid =
          income.annualSalary.isValid &&
          income.spouceAnnualSalary.isValid &&
          income.otherIncome.isValid;
        income.grossIncome.isValid = true;
      } else {
        this.validateGreaterThanZero(income.grossIncome);
        isIncomeValid = income.grossIncome.isValid;
      }
      return isIncomeValid && isExpenseValid;
    }
  }
};
</script>

<style lang="scss" scoped>
</style>