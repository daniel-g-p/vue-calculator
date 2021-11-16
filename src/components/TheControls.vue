<template>
  <div class="controls">
    <base-button
      v-for="button in buttons"
      :key="button.label"
      :class="`controls--${button.label}`"
      :color="button.class"
      @click="clickButton(button.label)"
      >{{ button.content }}</base-button
    >
  </div>
</template>

<script>
export default {
  setup(props, context) {
    const buttons = [
      { content: 1, label: "1", class: 1 },
      { content: 2, label: "2", class: 1 },
      { content: 3, label: "3", class: 1 },
      { content: 4, label: "4", class: 1 },
      { content: 5, label: "5", class: 1 },
      { content: 6, label: "6", class: 1 },
      { content: 7, label: "7", class: 1 },
      { content: 8, label: "8", class: 1 },
      { content: 9, label: "9", class: 1 },
      { content: 0, label: "0", class: 1 },
      { content: "+", label: "addition", class: 1 },
      { content: "-", label: "subtraction", class: 1 },
      { content: "/", label: "division", class: 1 },
      { content: "×", label: "mutliplication", class: 1 },
      { content: ".", label: "point", class: 1 },
      { content: "=", label: "equal", class: 3 },
      { content: "del", label: "delete", class: 2 },
      { content: "Clear", label: "clear", class: 2 },
    ];
    const clickButton = (label) => {
      context.emit("button-click", label);
    };
    return { buttons, clickButton };
  },
};
</script>

<style lang="scss" scoped>
@use "../assets/styles/index.scss" as *;
.controls {
  color: $color-text-2;
  background-color: $color-bg-2;
  border-radius: 0.5rem;
  padding: 1rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(5, 1fr);
  gap: 1rem;
  &--1 {
    grid-row: 3;
    grid-column: 1;
  }
  &--2 {
    grid-row: 3;
    grid-column: 2;
  }
  &--3 {
    grid-row: 3;
    grid-column: 3;
  }
  &--4 {
    grid-row: 2;
    grid-column: 1;
  }
  &--5 {
    grid-row: 2;
    grid-column: 2;
  }
  &--6 {
    grid-row: 2;
    grid-column: 3;
  }
  &--7 {
    grid-row: 1;
    grid-column: 1;
  }
  &--8 {
    grid-row: 1;
    grid-column: 2;
  }
  &--9 {
    grid-row: 1;
    grid-column: 3;
  }
  &--0 {
    grid-row: 4;
    grid-column: 2;
  }
  &--point {
    grid-row: 4;
    grid-column: 1;
  }
  &--division {
    grid-row: 4;
    grid-column: 3;
  }
  &--multiplication {
    grid-row: 4;
    grid-column: 4;
  }
  &--subtraction {
    grid-row: 3;
    grid-column: 4;
  }
  &--addition {
    grid-row: 2;
    grid-column: 4;
  }
  &--delete {
    grid-row: 1;
    grid-column: 4;
  }
  &--clear {
    grid-row: 5;
    grid-column: 1 / span 2;
  }
  &--equal {
    grid-row: 5;
    grid-column: 3 / span 2;
  }
}
</style>
