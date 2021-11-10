<template>
  <div>
    <button @click="randomizeCiv">Randomize!</button>

    <div>
      <p v-if="selectedCiv">Result: {{ selectedCiv }}</p>
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

    function randomizeCiv() {
      const civKeys = Object.keys(CivResult) as Array<keyof typeof CivResult>;

      const randomNum = Math.floor(Math.random() * civKeys.length);

      const selectedKey = civKeys[randomNum];

      selectedCiv.value = CivResult[selectedKey];
    }

    return { selectedCiv, randomizeCiv };
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
