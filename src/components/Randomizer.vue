<template>
  <div>
    <div class="random-btn__cotainer">
      <button
        class="btn btn--primary"
        :disabled="loading"
        @click="randomizeCiv"
      >
        Randomize!
      </button>
      <label for="no_duplicates">
        <input
          v-model="noDuplicates"
          type="checkbox"
          name="duplicates"
          id="no_duplicates "
        />
        No duplicates
      </label>
    </div>
    <div v-if="loading || selectedCiv" class="selection separated">
      <p v-if="loading">Loading...</p>
      <template v-else-if="selectedCiv">
        <p class="selected-civ">{{ selectedCiv }}</p>
        <button class="btn btn--secondary" @click="selectCiv">Select</button>
      </template>
    </div>

    <div v-if="selectedCivs.length" class="list-container separated">
      <ul class="bulleted">
        <li v-for="(item, index) in selectedCivs" :key="item + index">
          {{ item }}
        </li>
      </ul>
      <button
        class="btn btn--secondary"
        v-if="selectedCivs.length"
        @click="clearSelection"
      >
        Clear
      </button>
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
      }, 250);
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
.random-btn__cotainer {
  margin: 0 0 8px 0;
}
.selection {
  background-image: linear-gradient(0deg, #002845, #013f63);
  background-image: linear-gradient(#394766, #181c29);
  margin: 0 auto;
  padding: 8px 16px;
  display: flex;
  width: auto;
  align-items: center;
  justify-content: space-between;
}

.selected-civ {
  font-size: 1.3rem;
  margin: 0;
  margin-right: 8px;
}

.list-container {
  color: #c7c7c7;
  background-image: linear-gradient(#394766, #181c29);
  padding: 8px 16px;
}
</style>
