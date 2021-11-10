<template>
  <h1>A.O.E - Randomizer</h1>
  <Randomizer />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Randomizer from "./components/Randomizer.vue";

export default defineComponent({
  name: "App",
  components: {
    Randomizer,
  },
});
</script>

<style>
#app {
  font-family: "Open Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background-color: #0f1119;
}
h1,
h2,
h3,
p {
  color: #ffdf91;
}
</style>
