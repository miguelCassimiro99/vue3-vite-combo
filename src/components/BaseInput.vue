<template>
  <div class="input-wrap">
    <label v-if="label">{{ label }}</label>
    <input
      type="text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      v-bind="$attrs"
    >
  </div>
</template>
<script setup>
defineProps({
  label: {
    type: [String, Boolean],
    default: false,
  },
  modelValue: {
    type: String,
    default: ""
  }
})
</script>
<style scoped>
.input-wrap {
  display: flex;
  flex-direction: column;
}

.input-wrap input {
    padding: 8px 12px;
    font-size: 16px;
}

label {
  text-align: left;
}
</style>