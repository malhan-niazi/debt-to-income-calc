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
              <p>
                This Debt-to-Income Ratio calculator is provided to help you
                determine the percentage of how much you pay each month for your
                mortgage(s) compared to your total monthly gross income.
              </p>
              <p>
                This calculator returns information based on your inputs
                regarding your existing mortgage information. It is important
                that you provide accurate information in order to receive more
                realistic results.
              </p>
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
          <InputFieldComponent
            v-bind:inputField="expense.monthlyMortgagePayment"
            v-on:enter-value="validate"
            v-bind:isInvalid="
              !expense.checked && !expense.monthlyMortgagePayment.isValid
            "
            v-bind:isDisabled="expense.checked"
          ></InputFieldComponent>
          <div
            class="form-group row background--gray background--rounded padding margin--bottom"
          >
            <div class="col-sm-10">
              <div class="form-check">
                <input
                  :id="expense.radioOne.id"
                  v-model="expense.checked"
                  class="form-check-input"
                  type="radio"
                  :value="expense.radioOne.value"
                  :checked="expense.radioOne.isDefault"
                />
                <label class="form-check-label" :for="expense.radioOne.id">{{
                  expense.radioOne.label
                }}</label>
              </div>
              <div class="form-check">
                <input
                  :id="expense.radioTwo.id"
                  v-model="expense.checked"
                  class="form-check-input"
                  type="radio"
                  :value="expense.radioTwo.value"
                  :checked="expense.radioTwo.isDefault"
                />
                <label class="form-check-label" :for="expense.radioTwo.id">{{
                  expense.radioTwo.label
                }}</label>
              </div>
            </div>
          </div>
          <div v-if="expense.checked">
            <InputFieldComponent
              v-bind:inputField="expense.monthlyPayment"
              v-on:enter-value="validate"
              v-bind:isInvalid="!expense.monthlyPayment.isValid"
              v-bind:isDisabled="false"
            ></InputFieldComponent>
            <InputFieldComponent
              v-bind:inputField="expense.annualPropertyTax"
              v-on:enter-value="validate"
              v-bind:isInvalid="!expense.annualPropertyTax.isValid"
              v-bind:isDisabled="false"
            ></InputFieldComponent>
            <InputFieldComponent
              v-bind:inputField="expense.annualPropertyInsurance"
              v-on:enter-value="validate"
              v-bind:isInvalid="!expense.annualPropertyInsurance.isValid"
              v-bind:isDisabled="false"
            ></InputFieldComponent>
            <InputFieldComponent
              v-bind:inputField="expense.annualHoaFees"
              v-on:enter-value="validateOptionalField"
              v-bind:isInvalid="!expense.annualHoaFees.isValid"
              v-bind:isDisabled="false"
            ></InputFieldComponent>
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
          <InputFieldComponent
            v-bind:inputField="income.grossIncome"
            v-on:enter-value="validate"
            v-bind:isInvalid="!income.checked && !income.grossIncome.isValid"
            v-bind:isDisabled="income.checked"
          ></InputFieldComponent>
          <div
            class="form-group row background--gray background--rounded margin--bottom"
          >
            <div class="col-sm-10">
              <div class="form-check">
                <input
                  :id="income.radioOne.id"
                  v-model="income.checked"
                  class="form-check-input"
                  type="radio"
                  :value="income.radioOne.value"
                  :checked="income.radioOne.isDefault"
                />
                <label class="form-check-label" :for="income.radioOne.id">{{
                  income.radioOne.label
                }}</label>
              </div>
              <div class="form-check">
                <input
                  :id="income.radioTwo.id"
                  v-model="income.checked"
                  class="form-check-input"
                  type="radio"
                  :value="income.radioTwo.value"
                  :checked="income.radioTwo.isDefault"
                />
                <label class="form-check-label" :for="income.radioTwo.id">{{
                  income.radioTwo.label
                }}</label>
              </div>
            </div>
          </div>
          <div v-if="income.checked">
            <InputFieldComponent
              v-bind:inputField="income.annualSalary"
              v-on:enter-value="validate"
              v-bind:isInvalid="!income.annualSalary.isValid"
              v-bind:isDisabled="false"
            ></InputFieldComponent>
            <InputFieldComponent
              v-bind:inputField="income.spouceAnnualSalary"
              v-on:enter-value="validate"
              v-bind:isInvalid="!income.spouceAnnualSalary.isValid"
              v-bind:isDisabled="false"
            ></InputFieldComponent>
            <InputFieldComponent
              v-bind:inputField="income.otherIncome"
              v-on:enter-value="validate"
              v-bind:isInvalid="!income.otherIncome.isValid"
              v-bind:isDisabled="false"
            ></InputFieldComponent>
          </div>
          <div class="form-group row">
            <div class="col">
              <div class="row">
                <button class="btn btn-primary font-weight-bold">
                  Calculate
                </button>
              </div>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import InputFieldComponent from "./InputFieldComponent";

export default {
  name: "InputComponent",
  components: {
    InputFieldComponent
  },
  data() {
    return {
      expense: {
        monthlyMortgagePayment: {
          id: "monthlyMortgagePayment",
          value: null,
          isValid: true,
          label: "Total First Mortgage Monthly Payment(s)",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: true,
          desc:
            "This should include your first monthly mortgage payment, as well as any additional mortgage payments you may have. It should also include principal, interest, taxes, insurance and homeowner's association fees. If you have an escrow account set up on your first mortgage, these costs will be included in your monthly payment."
        },
        monthlyPayment: {
          id: "monthlyPayment",
          value: null,
          isValid: true,
          label: "Monthly Payment",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: false,
          desc: ""
        },
        annualPropertyTax: {
          id: "annualPropertyTax",
          value: null,
          isValid: true,
          label: "Annual Property Taxes",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: false,
          desc: ""
        },
        annualPropertyInsurance: {
          id: "annualPropertyInsurance",
          value: null,
          isValid: true,
          label: "Annual Property Insurance",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: false,
          desc: ""
        },
        annualHoaFees: {
          id: "annualHoaFees",
          value: null,
          isValid: true,
          label: "Annual Home Owner's Association Fees",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount (Optional)",
          errorMsg: "This field must be numeric.",
          hasDesc: false,
          desc: ""
        },
        checked: false,
        radioOne: {
          id: "expenseRadio1",
          value: false,
          isDefault: true,
          label: "Fill out consolidated Mortgage Monthly Payment(s) above."
        },
        radioTwo: {
          id: "expenseRadio2",
          value: true,
          isDefault: false,
          label: "If not, click here and fill in the information below."
        }
      },
      income: {
        grossIncome: {
          id: "grossIncome",
          value: null,
          isValid: true,
          label: "Gross Monthly Income",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: false,
          desc: ""
        },
        annualSalary: {
          id: "annualSalary",
          value: null,
          isValid: true,
          label: "Annual Salary",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: false,
          desc: ""
        },
        spouceAnnualSalary: {
          id: "spouceAnnualSalary",
          value: null,
          isValid: true,
          label: "Spouse or Partner's Annual Salary",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: false,
          desc: ""
        },
        otherIncome: {
          id: "otherIncome",
          value: null,
          isValid: true,
          label: "Other Annual Income",
          hasIcon: true,
          icon: "$",
          type: "text",
          placeHolder: "Enter Amount",
          errorMsg: "This field is required and must be numeric.",
          hasDesc: false,
          desc: ""
        },
        checked: false,
        radioOne: {
          id: "incomeRadio1",
          value: false,
          isDefault: true,
          label: "Fill out consolidated Mortgage Monthly Payment(s) above."
        },
        radioTwo: {
          id: "incomeRadio2",
          value: true,
          isDefault: false,
          label:
            "If you are unsure of this amount, click here and fill in the information below."
        }
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