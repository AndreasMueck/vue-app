<script setup>
import { ref, onMounted } from 'vue'

const dichte = ref('');
const name = ref('');
const werkstoff = ref('');

const materialsList = ref([
      { dichte: "7880", name: "Edelstahl"},
      { dichte: "7850", name: "Federstahl"},
      { dichte: "8200", name: "Messing"},
      { dichte: "8620", name: "Bronze"},
      { dichte: "2700", name: "Aluminium"},
])

const onSelectChange = (event) => {
  dichte.value = event.target.value;
  name.value = event.target.options[event.target.options.selectedIndex].text;
}

onMounted(() => {
  werkstoff.value = 8620;
  name.value = "Bronze";
})

</script>

<template>
  <div>
    <p>
      <select v-model="werkstoff" @change="onSelectChange($event)">
        <option v-for="material in materialsList" :key="material.dichte" :value="material.dichte">
          {{ material.name }}
        </option>
      </select>
    </p>
    <p>
      Dichte: {{ werkstoff }}
    </p>
    <p>
      Name: {{ name }}
    </p>
  </div>
</template>