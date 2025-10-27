<template>
  <label class="label">
    <span class="text">{{ label }}</span>
    <select v-model="model" class="select">
      <option disabled value="">-- Select an option --</option>
      <option v-for="option in options" :value="option.value" class="option">{{ option.label }}</option>
    </select>
  </label>
</template>

<script setup>
const model = defineModel();

defineProps({
  options: {
    type: Array,
    required: true
  },
  label: {
    type: String,
    required: true
  }
})
</script>

<style scoped>
.label {
  display: block;
}

.text {
  margin-bottom: 4px;
  display: block;
  font-weight: 600;
  color: #757575;
}

.select {
  width: 100%;
  padding: 16px;
  display: block;
  border: 2px solid #d4d6d8;
  background-image: url("../assets/arrow.svg");
  background-position: calc(100% - 16px);
  background-repeat: no-repeat;
  appearance: none;
  cursor: pointer;
}

.option {
  cursor: pointer;
}
</style>