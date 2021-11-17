<template>
  <div class="output">
    <p class="output__result" :class="highlightClass">
      <slot></slot>
    </p>
  </div>
</template>

<script>
import { computed } from "vue";

export default {
  props: {
    highlighted: {
      type: Boolean,
      required: true,
    },
  },
  setup(props) {
    const highlightClass = computed(() => {
      return { "output__result--highlight": props.highlighted };
    });
    return { highlightClass };
  },
};
</script>

<style lang="scss" scoped>
@use "../assets/styles/index.scss" as *;
.output {
  font-size: 2rem;
  color: $color-text-2;
  background-color: $color-bg-2;
  display: block;
  height: 5rem;
  text-align: right;
  position: relative;
  border-radius: 0.5rem;
  max-width: 20rem;
  position: relative;
  overflow: hidden;
  &__result {
    white-space: nowrap;
    text-align: right;
    position: absolute;
    top: 50%;
    right: 1.5rem;
    transform: translateY(-50%);
    &--highlight {
      animation: highlight 0.5s linear forwards;
    }
  }
}

@keyframes highlight {
  0% {
    opacity: 1;
  }
  25% {
    opacity: 0.5;
  }
  50% {
    opacity: 1;
  }
  75% {
    opacity: 0.5;
  }
  100% {
    opacity: 1;
  }
}
</style>
