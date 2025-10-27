<template>
  <button type="button" class="button" :disabled="disabled">
    <slot />
  </button>
</template>

<script setup>
defineProps({
  disabled: {
    type: Boolean,
    default: false
  }
});
</script>

<style scoped>
.button {
  padding: 10px 16px;
  background: #00aa28;
  border: 2px solid transparent;
  border-radius: 4px;
  color: #fffaf5;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.5s ease;
}

.button:disabled {
  cursor: not-allowed;
  opacity: 0.4;
}

.button:hover,
.button:active {
  color: #00aa28;
  border: 2px solid #00aa28;
  background: #fffaf5;
}
</style>