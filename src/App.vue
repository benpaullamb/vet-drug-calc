<template>
  <div class="container">
    <Header />

    <Section>
      <TextField v-model="weight" label="Patient Weight (kg)" type="number" :min="0"></TextField>
    </Section>

    <Section dark>
      <Dropdown label="Opiate" v-model="opiate" :options="['Methadone']" />
    </Section>

    <Section>
      <Button @click="calculate">Calculate</Button>
    </Section>

    <Section dark>
      <span class="dose">{{ dose }}ml</span>
      <span class="perAgent">per agent</span>
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

const weight = ref(0);
const opiate = ref("Methadone");
const dose = ref(0);

function calculate() {
  if (!weight.value) {
    return;
  }

  const doseWanted = 0.2; // mg/kg
  const concentration = 5; // mg/ml
  const totalDose = doseWanted * weight.value; // mg
  const volume = totalDose / concentration; // ml
  dose.value = volume;
}
</script>

<style scoped>
.container {
  height: 100dvh;
}

.dose {
  display: block;
  font-size: 20px;
}

.perAgent {
  display: block;
}
</style>
