<template>
  <details :class="{ disabled: disabled }">
    <summary class="summary">
      <span class="label">{{ label }}</span>
    </summary>
    <div class="content">
      <slot />
    </div>
  </details>
</template>

<script setup>
defineProps({
  label: {
    type: String,
    required: true
  },
  disabled: {
    type: Boolean,
    default: false
  }
});
</script>

<style scoped>
.details {
  cursor: pointer;
}

.content {
  padding: 8px;
  overflow: auto;
}

.disabled {
  pointer-events: none;
  user-select: none;
  cursor: default;
}

.label {
  font-size: 14px;
  padding-left: 4px;
}

.disabled .summary,
.disabled .label {
  color: grey;
}
</style>