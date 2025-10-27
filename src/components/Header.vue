<template>
  <header class="header">
    <div class="left">
      <div class="logoContainer">
        <img :src="logo" alt="Vets for Pets logo" class="logo" />
        <span class="location">Ruislip</span>
      </div>
      
      <span class="description">Pre-med estimator tool for reference</span>
    </div>

    <span class="version">v1.1.0</span>
  </header>
</template>

<script setup>
import logo from "../assets/vets-for-pets-logo.png";
</script>

<style scoped>
.header {
  padding: 16px;
  box-shadow: 0 0 8px 0 lightgrey;
  display: flex;
  justify-content: space-between;
  align-items: end;
  position: relative;
  z-index: 1;
}

.logoContainer {
  display: flex;
  align-items: end;
  gap: 8px;
}

.logo {
  width: 150px;
  display: block;
  margin-bottom: 4px;
}

.location {
  font-size: 14px;
  font-weight: bold;
}

.description {
  display: block;
  font-size: 14px;
}

.version {
  font-size: 12px;
}
</style>