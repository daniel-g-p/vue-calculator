<template>
  <button class="button" :class="colorClass">
    <div class="button__container"><slot></slot></div>
    <div class="button__background"></div>
  </button>
</template>

<script>
import { computed } from "vue";

export default {
  props: {
    color: {
      type: Number,
      default: 1,
      validator(value) {
        return [1, 2, 3].includes(value);
      },
    },
  },
  setup(props) {
    const colorClass = computed(() => {
      switch (props.color) {
        case 1:
          return { "button--color-1": true };
        case 2:
          return { "button--color-2": true };
        case 3:
          return { "button--color-3": true };
        default:
          return { "button--color-1": true };
      }
    });
    return { colorClass };
  },
};
</script>

<style lang="scss" scoped>
@use "../assets/styles/index.scss" as *;
.button {
  position: relative;
  z-index: 1;
  text-transform: uppercase;
  font-size: 0.875rem;
  &--color-1 {
    color: $color-text-1;
    .button__container {
      background-color: $color-keys-5;
    }
    .button__background {
      background-color: $color-keys-6;
    }
  }
  &--color-2 {
    color: $color-text-2;
    .button__container {
      background-color: $color-keys-1;
    }
    .button__background {
      background-color: $color-keys-2;
    }
  }
  &--color-3 {
    color: $color-text-2;
    .button__container {
      background-color: $color-keys-3;
    }
    .button__background {
      background-color: $color-keys-4;
    }
  }
  &__container {
    padding: 0.75em 0.25em;
    border-radius: 0.25rem;
    position: relative;
    cursor: pointer;
    transition: transform 0.125s ease;
    &:hover,
    &:focus {
      transform: translateY(0.25rem);
    }
    @include responsive($screen-tablet-s) {
      padding: 0.75em 1em;
    }
  }
  &__background {
    display: block;
    width: 100%;
    height: 100%;
    border-radius: 0.25rem;
    position: absolute;
    z-index: -1;
    top: 0.25rem;
    left: 0;
  }
}
</style>
