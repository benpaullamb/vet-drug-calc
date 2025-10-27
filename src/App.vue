<template>
  <div class="container">
    <Header />

    <Section class="form">
      <TextField label="Patient Weight (kg)" v-model="weight" type="number" :min="0"></TextField>

      <Dropdown label="Agent" v-model="agent" :options="agentNames" />

      <TextField label="Dose (mg/kg)" v-model="dose" type="number" :min="0"></TextField>

      <div>
        <Button @click="calculate" :disabled="!weight || !agent || !dose">Calculate</Button>
      </div>
    </Section>

    <Section dark>
      <span class="dose" :class="{ disabled: !volumeRequired }">{{ volumeRequired }} mL <span class="perAgent"
          :class="{ disabled: !volumeRequired }">per
          agent</span></span>

      <Expandable label="Calculation workings" :disabled="!volumeRequired">
        <pre>
Dose (mg) = Patient weight (kg) &times; Dose wanted (mg/kg)
Dose (mg) = {{ weight }} kg &times; {{ dose }} mg/kg = {{ weight * dose }} mg

Volume required (mL) = Dose (mg) &divide; Concentration (mg/mL)
Volume required (mL) = {{ weight * dose }} mg &divide; {{ concentration }} mg/mL = {{ volumeRequired }} mL</pre>
      </Expandable>
    </Section>

    <Footer />
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';
import { agents } from './assets/agents.json';
import Header from './components/Header.vue';
import Section from './components/Section.vue';
import Footer from './components/Footer.vue';
import Button from './components/Button.vue';
import TextField from './components/TextField.vue';
import Dropdown from './components/Dropdown.vue';
import Expandable from './components/Expandable.vue';

const agentNames = agents.map(agent => ({
  label: `${agent.name} (${agent.brandName})`,
  value: agent.name
}));
const weight = ref(0);
const dose = ref(0);
const concentration = ref(5);
const agent = ref("");
const volumeRequired = ref(0);

watch(agent, (value) => {
  const agentInfo = agents.find(agent => agent.name === value);
  dose.value = agentInfo.dose;
});

function calculate() {
  if (!weight.value) {
    return;
  }

  const totalDose = dose.value * weight.value;
  volumeRequired.value = totalDose / concentration.value;
}
</script>

<style scoped>
.container {
  height: 100dvh;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.dose {
  display: block;
  margin-bottom: 32px;
  font-size: 24px;
}

.disabled {
  color: grey;
}
</style>
