<template>
  <label class="label">
    <span class="text">{{ label }}</span>
    <input v-model="model" class="input" :type="type" :min="min" />
  </label>
</template>

<script setup>
const model = defineModel();

defineProps({
  label: {
    type: String,
    required: true
  },
  type: {
    type: String,
    default: "text"
  },
  min: {
    type: Number,
    default: 0
  }
});
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

.input {
  width: 100%;
  padding: 16px;
  display: block;
  border: 2px solid #d4d6d8;
}
</style>