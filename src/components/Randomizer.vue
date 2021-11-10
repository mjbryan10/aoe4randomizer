<template>
  <div>
    <button :disabled="loading" @click="randomizeCiv">Randomize!</button>
    <label for="no_duplicates">
      <input
        v-model="noDuplicates"
        type="checkbox"
        name="duplicates"
        id="no_duplicates "
      />
      No duplicates
    </label>
    <div>
      <p v-if="loading">Loading...</p>
      <template v-else-if="selectedCiv">
        <p>{{ selectedCiv }}</p>
        <button @click="selectCiv">select</button>
      </template>
    </div>

    <div>
      <ul>
        <li v-for="(item, index) in selectedCivs" :key="item + index">
          {{ item }}
        </li>
      </ul>
      <button v-if="selectedCivs.length" @click="clearSelection">Clear</button>
    </div>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, computed } from "vue";

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
    const availableCivs = computed<CivResult[]>(() => Object.values(CivResult));
    const selectedCiv = ref<CivResult | null>(null);
    const loading = ref(false);

    const noDuplicates = ref(false);

    function randomizeCiv() {
      loading.value = true;

      const civs = noDuplicates.value
        ? filteredCivs.value
        : availableCivs.value;

      const randomNum = Math.floor(Math.random() * civs.length);

      setTimeout(() => {
        selectedCiv.value = civs[randomNum];
        loading.value = false;
      }, 500);
    }

    const selectedCivs = ref<CivResult[]>([]);
    const filteredCivs = computed<CivResult[]>(() =>
      availableCivs.value.filter((civ) => !selectedCivs.value.includes(civ))
    );

    function selectCiv() {
      if (selectedCiv.value) selectedCivs.value.push(selectedCiv.value);
    }

    function clearSelection() {
      selectedCivs.value = [];
    }

    return {
      selectedCiv,
      randomizeCiv,
      loading,
      selectCiv,
      selectedCivs,
      clearSelection,
      noDuplicates,
    };
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
