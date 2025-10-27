<template>
  <div class="section" :class="{
    light: !dark,
    dark: dark
  }">
    <slot />
  </div>
</template>

<script setup>
defineProps({
  dark: {
    type: Boolean,
    default: false
  }
});
</script>

<style scoped>
.section {
  padding: 20px;
}

.light {
  background: #fffaf5;
}

.dark {
  background: #f0e6dc;
}
</style>