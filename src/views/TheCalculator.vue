<template>
  <main class="calculator">
    <div class="calculator__logo">
      <the-logo></the-logo>
    </div>
    <div class="calculator__toggle">
      <the-toggle></the-toggle>
    </div>
    <div class="calculator__output">
      <the-output>{{ expression }}</the-output>
    </div>
    <div class="calculator__controls">
      <the-controls @button-click="clickButton"></the-controls>
    </div>
  </main>
</template>

<script>
import TheLogo from "../components/TheLogo.vue";
import TheToggle from "../components/TheToggle.vue";
import TheOutput from "../components/TheOutput.vue";
import TheControls from "../components/TheControls.vue";

import { ref } from "vue";

export default {
  components: {
    TheLogo,
    TheToggle,
    TheOutput,
    TheControls,
  },
  setup() {
    let result = 0;
    let operationPending = true;
    const expression = ref("");
    const replaceLastCharacter = (character) => {
      const expressionLength = expression.value.length;
      expression.value = `${expression.value.slice(
        0,
        expressionLength - 1
      )}${character}`;
    };
    const setOperation = (operationSymbol) => {
      if (operationPending) {
        replaceLastCharacter(operationSymbol);
      } else {
        expression.value += operationSymbol;
        operationPending = true;
      }
    };
    const clickButton = (label) => {
      if (label === "clear") {
        result = 0;
        expression.value = "";
        operationPending = true;
      } else if (label === "equal") {
        expression.value = `${result}`;
      } else if (label === "delete") {
        const expressionLength = expression.value.length;
        expression.value = expression.value.slice(0, expressionLength - 1);
        const lastCharacter = parseInt(
          expression.value.slice(expressionLength - 2)
        );
        operationPending = !lastCharacter && lastCharacter !== 0;
      } else if (label === "point") {
        expression.value += operationPending ? "0." : ".";
      } else if (label === "addition") {
        setOperation("+");
      } else if (label === "subtraction") {
        setOperation("-");
      } else if (label === "mutliplication") {
        setOperation("×");
      } else if (label === "division") {
        setOperation("/");
      } else {
        expression.value += label;
        operationPending = false;
      }
    };
    return { expression, clickButton };
  },
};
</script>

<style lang="scss" scoped>
@use "../assets/styles/index.scss" as *;
.calculator {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  width: 100%;
  max-width: 20rem;
  margin: 1rem;
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
