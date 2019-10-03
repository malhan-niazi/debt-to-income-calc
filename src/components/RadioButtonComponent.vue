<template>
  <div>
    <div class="form-check">
      <input
        :id="radio.id"
        v-model="selected"
        class="form-check-input"
        type="radio"
        :value="radio.value"
        :checked="radio.isDefault"
      />
      <label class="form-check-label" :for="radio.id">{{ radio.label }}</label>
    </div>
  </div>
</template>
<script>
export default {
  name: "RadioButtonComponent",
  props: {
    radio: Object,
    selected: Boolean
  }
};
</script>
<style lang="">
</style>