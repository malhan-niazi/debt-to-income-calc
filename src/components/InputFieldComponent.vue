<template>
  <div>
    <div
      class="form-group row background--gray background--rounded margin--bottom"
    >
      <label
        :for="inputField.id"
        class="col-sm-6 padding-right col-form-label font-weight-bold"
        >{{ inputField.label }}</label
      >
      <div class="col-sm-6 padding-right">
        <div class="input-group">
          <div v-if="inputField.icon" class="input-group-prepend">
            <span class="input-group-text">{{ inputField.icon }}</span>
          </div>
          <input
            :id="inputField.id"
            v-model="inputField.value"
            :type="inputField.type"
            class="form-control rounded-right"
            :placeholder="inputField.placeHolder"
            :class="{ 'is-invalid': isInvalid }"
            :disabled="isDisabled"
            @input="$emit('enter-value', inputField)"
          />
          <div class="invalid-feedback">{{ inputField.errorMsg }}</div>
        </div>
      </div>
      <p v-if="inputField.desc" class="padding-p">{{ inputField.desc }}</p>
    </div>
  </div>
</template>
<script>
export default {
  name: "InputFieldComponent",
  props: {
    inputField: Object,
    isInvalid: Boolean,
    isDisabled: Boolean
  }
};
</script>
<style lang="sass">

</style>