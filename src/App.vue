<template>
  <div class="app">
    <the-calculator></the-calculator>
  </div>
</template>

<script>
import TheCalculator from "./views/TheCalculator.vue";

export default {
  components: {
    TheCalculator,
  },
};
</script>

<style lang="scss">
@use "./assets/styles/index.scss" as *;
@include font-face("Spartan", "Spartan-Bold", 700);
@include css-reset();
:root {
  --color-background-1: hsl(222, 26%, 31%);
  --color-background-2: hsl(223, 31%, 20%);
  --color-background-3: hsl(224, 36%, 15%);
  --color-keys-1: hsl(225, 21%, 49%);
  --color-keys-2: hsl(224, 28%, 35%);
  --color-keys-3: hsl(6, 63%, 50%);
  --color-keys-4: hsl(6, 70%, 34%);
  --color-keys-5: hsl(30, 25%, 89%);
  --color-keys-6: hsl(28, 16%, 65%);
  --color-text-1: hsl(221, 14%, 31%);
  --color-text-2: hsl(0, 0%, 100%);
}
html {
  font: 400 100%/1 "Spartan", sans-serif;
}
.app {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $color-bg-1;
}
</style>
