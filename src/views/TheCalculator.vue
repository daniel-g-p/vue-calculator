<template>
  <main class="calculator">
    <div class="calculator__logo">
      <the-logo></the-logo>
    </div>
    <div class="calculator__toggle">
      <the-toggle></the-toggle>
    </div>
    <div class="calculator__output">
      <the-output></the-output>
    </div>
    <div class="calculator__controls">
      <the-controls></the-controls>
    </div>
  </main>
</template>

<script>
import TheLogo from "../components/TheLogo.vue";
import TheToggle from "../components/TheToggle.vue";
import TheOutput from "../components/TheOutput.vue";
import TheControls from "../components/TheControls.vue";

export default {
  components: {
    TheLogo,
    TheToggle,
    TheOutput,
    TheControls,
  },
  setup() {},
};
</script>

<style lang="scss" scoped>
@use "../assets/styles/index.scss" as *;
.calculator {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  max-width: 24rem;
  &__toggle {
    justify-self: end;
  }
  &__output {
    grid-column: span 2;
  }
  &__controls {
    grid-column: span 2;
  }
}
</style>
