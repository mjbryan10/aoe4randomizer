<template>
  <div>
    <button :disabled="loading" @click="randomizeCiv">Randomize!</button>

    <div>
      <p v-if="loading">Loading...</p>
      <p v-else-if="selectedCiv">Result: {{ selectedCiv }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";

enum CivResult {
  Abbasid = "Abbasid Dynasty",
  China = "China",
  Dehli = "Dehli Sultanate",
  English = "English",
  French = "French",
  HolyRomanEmpire = "Holy roman empire",
  Mongols = "Mongols",
  Rus = "Rus",
}
export default defineComponent({
  name: "Radomizer",
  setup: () => {
    const selectedCiv = ref<CivResult | null>(null);
    const loading = ref(false);

    function randomizeCiv() {
      loading.value = true;
      const civKeys = Object.keys(CivResult) as Array<keyof typeof CivResult>;

      const randomNum = Math.floor(Math.random() * civKeys.length);

      const selectedKey = civKeys[randomNum];

      setTimeout(() => {
        selectedCiv.value = CivResult[selectedKey];
        loading.value = false;
      }, 500);
    }

    return { selectedCiv, randomizeCiv, loading };
  },
});
</script>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
