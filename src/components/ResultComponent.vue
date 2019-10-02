<template>
  <div>
    <div id="result" class="row margin--bottom">
      <div class="col">
        <div class="row padding-label color--blue padding-left--none">
          <h4>Your Debt-to-Income Information</h4>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="row padding-label padding-left--none">
          <h4>Please Note:</h4>
        </div>
        <div class="row">
          <p>These results have been calculated based on your inputs regarding your existing mortgage information. Your mortgage company may consider additional factors in determining your Debt-to-Income Ratio.</p>
          <p>Please save this information (as a PDF document) or email it to yourself, so that you may have it as a reference when you speak with your mortgage company or a housing counselor.</p>
          <p>Every situation is different. Contact your mortgage company or a housing counselor to determine your exact results and truly know your options.</p>
        </div>
      </div>
    </div>
    <div class="form-group row background--gray background--rounded padding margin--bottom">
      <label
        for="income4"
        class="col-sm-6 padding-right col-form-label font-weight-bold"
      >First Mortgage Monthly Payment</label>
      <div class="col-sm-6 padding-right">
        <div class="input-group">
          <span class="form-control-plaintext">${{ formatNumber(result.expense) }}</span>
        </div>
      </div>
    </div>
    <div class="form-group row background--gray background--rounded padding margin--bottom">
      <label
        for="income4"
        class="col-sm-6 padding-right col-form-label font-weight-bold"
      >Total Gross Monthly Income</label>
      <div class="col-sm-6 padding-right">
        <div class="input-group">
          <span class="form-control-plaintext">${{ formatNumber(result.income) }}</span>
        </div>
      </div>
    </div>
    <div class="form-group row background--gray background--rounded padding margin--bottom">
      <label
        for="income4"
        class="col-sm-6 padding-right col-form-label font-weight-bold color--blue"
      >Debt-to-Income Ratio</label>
      <div class="col-sm-6 padding-right">
        <div class="input-group">
          <span class="form-control-plaintext">{{ result.ratio }}%</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResultComponent",
  props: {
    result: Object
  },
  methods: {
    formatNumber(n) {
      return Number(n).toLocaleString();
    }
  }
};
</script>

<style lang="scss">
</style>