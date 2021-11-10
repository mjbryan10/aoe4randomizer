<template>
  <div class="page-container">
    <h1>A.O.E. IV - Randomizer</h1>
    <Randomizer />
  </div>
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

<style lang="scss">
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

.page-container {
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
}

h1,
h2,
h3 {
  font-family: "EB Garamond", serif;
}

h1,
h2,
h3,
p {
  color: #ffdf91;
}

.bulleted {
  padding: 0;
  list-style: none;
  margin: 0 0 1.5rem;
  text-align: left;
  li {
    text-indent: -1em;
    margin-left: 1em;
  }
  li::before {
    color: inherit;
    width: 1rem;
    text-indent: 0;
    display: inline-block;
    content: "";
    width: 0.4em;
    height: 0.4em;
    border-radius: 50%;
    background: -webkit-gradient(
      linear,
      left top,
      left bottom,
      from(#e7c067),
      to(#b8862d)
    );
    background: -webkit-linear-gradient(top, #e7c067, #b8862d);
    background: -o-linear-gradient(top, #e7c067, #b8862d);
    background: linear-gradient(180deg, #e7c067, #b8862d);
    margin-right: 0.6em;
    vertical-align: top;
    margin-top: calc(0.75rem - 0.2em);
  }
}

.highlight {
  background-image: linear-gradient(0deg, #002845, #013f63);
}

.btn {
  font-family: "EB Garamond", serif;
  font-weight: 700;
  font-size: 1rem;
  padding: 0.375rem 1.125rem;
  line-height: 1.5rem;
  z-index: 1;
  position: relative;
  &:hover {
    cursor: pointer;
  }
  &--primary {
    min-width: 140px;
    color: #45281f;
    -webkit-box-shadow: 0 0.25rem 0.5rem rgb(0 0 0 / 60%);
    box-shadow: 0 0.25rem 0.5rem rgb(0 0 0 / 60%);
    text-shadow: 1px 1px 2px rgb(255 223 145 / 80%);
    border-color: #ffdf91;
    background: -webkit-gradient(
      linear,
      left top,
      left bottom,
      from(#e7c067),
      to(#b8862d)
    );
    background: -webkit-linear-gradient(top, #e7c067, #b8862d);
    background: -o-linear-gradient(top, #e7c067, #b8862d);
    background: linear-gradient(180deg, #e7c067, #b8862d);

    &:hover {
      background-image: linear-gradient(0deg, #002845, #013f63);
      border-color: #ffdf91;
      color: #c7c7c7;
      -webkit-box-shadow: 0;
      box-shadow: 0;
      text-shadow: none;
    }
  }
  &--secondary {
    background-image: linear-gradient(0deg, #002845, #013f63);
    border-color: #ffdf91;
    color: #c7c7c7;
    &:hover {
      background: -webkit-gradient(
        linear,
        left top,
        left bottom,
        from(#e7c067),
        to(#b8862d)
      );
      background: -webkit-linear-gradient(top, #e7c067, #b8862d);
      background: -o-linear-gradient(top, #e7c067, #b8862d);
      background: linear-gradient(180deg, #e7c067, #b8862d);
      color: #45281f;
    }
  }
}

.separated {
  border-width: 2 px 0 0;
  border-image-slice: 1;
  border-image-source: linear-gradient(
    90deg,
    rgba(184, 134, 45, 0),
    #b8862d,
    #ffdf91,
    #b8862d,
    rgba(184, 134, 45, 0)
  );
  border-style: solid;
  margin: 4px 0;
}
</style>
