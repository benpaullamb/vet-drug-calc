<template>
  <div class="container">
    <Header />

    <Section>
      <TextField label="Patient Weight (kg)" type="number" :min="0"></TextField>
    </Section>

    <Section dark>
      <Dropdown label="Dropdown" v-model="dropdownValue" :options="['Dog', 'Cat', 'Pig']" />

    </Section>

    <Section>
      {{ dropdownValue }}
      <Button>Calculate</Button>
    </Section>

    <Footer />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue';
import Section from './components/Section.vue';
import Footer from './components/Footer.vue';
import Button from './components/Button.vue';
import TextField from './components/TextField.vue';
import Dropdown from './components/Dropdown.vue';

const dropdownValue = ref("");
</script>

<style scoped>
.container {
  height: 100dvh;
}
</style>
