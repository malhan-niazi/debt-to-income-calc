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
                    <input type="text" class="form-control" />
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <div class="form-check">
                    <input class="form-check-input" type="checkbox" id="expenseInfoChecked" />
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
                    <input type="text" class="form-control" />
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
                    <input type="text" class="form-control" />
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
                    <input type="text" class="form-control" />
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
                    <input type="text" class="form-control" />
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
                    <input type="text" class="form-control" />
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <div class="form-check">
                    <input class="form-check-input" type="checkbox" id="incomeInfoChecked" />
                    <label
                      class="form-check-label"
                      for="gridCheck"
                    >click here to fill out individual items below</label>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Gross Monthly Income</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input type="text" class="form-control" />
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Gross Monthly Income</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input type="text" class="form-control" />
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="form-group col">
                  <label for="text">Gross Monthly Income</label>
                  <div class="input-group">
                    <div class="input-group-prepend">
                      <span class="input-group-text">$</span>
                    </div>
                    <input type="text" class="form-control" />
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
                      <span class="form-control">{{ total }}</span>
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
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
