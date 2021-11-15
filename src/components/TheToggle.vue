<template>
  <div class="toggle">
    <div class="toggle__label">Theme</div>
    <div class="toggle__controls" @click="toggleTheme">
      <div class="toggle__numbers">
        <div class="toggle__number">1</div>
        <div class="toggle__number">2</div>
        <div class="toggle__number">3</div>
      </div>
      <div class="toggle__bar">
        <div class="toggle__ball" :class="ballClass"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, reactive, computed, watch } from "vue";

export default {
  setup() {
    const cssVariables = reactive(document.documentElement.style);
    const themeColors = {
      theme1: {
        bg1: "hsl(222, 26%, 31%)",
        bg2: "hsl(223, 31%, 20%)",
        bg3: "hsl(224, 36%, 15%)",
        keys1: "hsl(225, 21%, 49%)",
        keys2: "hsl(224, 28%, 35%)",
        keys3: "hsl(6, 63%, 50%)",
        keys4: "hsl(6, 70%, 34%)",
        keys5: "hsl(30, 25%, 89%)",
        keys6: "hsl(28, 16%, 65%)",
        text1: "hsl(221, 14%, 31%)",
        text2: "hsl(0, 0%, 100%)",
      },
      theme2: {
        bg1: "hsl(0, 0%, 90%)",
        bg2: "hsl(0, 5%, 81%)",
        bg3: "hsl(0, 0%, 93%)",
        keys1: "hsl(185, 42%, 37%)",
        keys2: "hsl(185, 58%, 25%)",
        keys3: "hsl(25, 98%, 40%)",
        keys4: "hsl(25, 99%, 27%)",
        keys5: "hsl(45, 7%, 89%)",
        keys6: "hsl(35, 11%, 61%)",
        text1: "hsl(60, 10%, 19%)",
        text2: "hsl(0, 0, 100%)",
      },
      theme3: {
        bg1: "hsl(268, 75%, 9%)",
        bg2: "hsl(268, 71%, 12%)",
        bg3: "hsl(268, 71%, 12%)",
        keys1: "hsl(281, 89%, 26%)",
        keys2: "hsl(285, 91%, 52%)",
        keys3: "hsl(176, 100%, 44%)",
        keys4: "hsl(177, 92%, 70%)",
        keys5: "hsl(268, 47%, 21%)",
        keys6: "hsl(290, 70%, 36%)",
        text1: "hsl(198, 20%, 13%)",
        text2: "hsl(52, 100%, 62%)",
      },
    };
    const themeNumber = ref(1);
    const ballClass = computed(() => {
      switch (themeNumber.value) {
        case 1: {
          return { "toggle__ball--1": true };
        }
        case 2: {
          return { "toggle__ball--2": true };
        }
        case 3: {
          return { "toggle__ball--3": true };
        }
        default: {
          return { "toggle__ball--1": true };
        }
      }
    });
    const toggleTheme = () => {
      if (themeNumber.value < 3) {
        themeNumber.value++;
      } else {
        themeNumber.value = 1;
      }
    };
    const setColor = (colorName, colorCode) => {
      cssVariables.setProperty(colorName, colorCode);
    };
    watch(themeNumber, (newValue) => {
      const colors = themeColors[`theme${newValue}`];
      setColor("--color-background-1", colors.bg1);
      setColor("--color-background-2", colors.bg2);
      setColor("--color-keys-1", colors.keys1);
      setColor("--color-keys-2", colors.keys2);
      setColor("--color-keys-3", colors.keys3);
      setColor("--color-keys-4", colors.keys4);
      setColor("--color-keys-5", colors.keys5);
      setColor("--color-keys-6", colors.keys6);
      setColor("--color-text-1", colors.text1);
      setColor("--color-text-2", colors.text2);
    });
    return { ballClass, toggleTheme };
  },
};
</script>

<style lang="scss" scoped>
@use "../assets/styles/index.scss" as *;
.toggle {
  display: flex;
  align-items: center;
  font-size: 0.625rem;
  text-transform: uppercase;
  color: $color-text-2;
  &__label {
    margin-right: 0.25rem;
  }
  &__controls {
    display: flex;
    flex-direction: column;
    position: relative;
    cursor: pointer;
    &:hover {
      .toggle__bar {
        background-color: $color-keys-1;
      }
    }
  }
  &__numbers {
    position: absolute;
    width: 100%;
    transform: translateY(-100%);
    display: flex;
    justify-content: space-around;
    padding: 0.25rem 0;
  }
  &__bar {
    background-color: $color-bg-3;
    display: block;
    height: 1.25rem;
    width: 3.25rem;
    border-radius: 0.75rem;
    padding: 0.25rem;
  }
  &__ball {
    width: 0.75rem;
    height: 0.75rem;
    border-radius: 50%;
    background-color: $color-keys-3;
    transition: margin-left 0.25s ease;
    &--1 {
      margin-left: 0;
    }
    &--2 {
      margin-left: 1rem;
    }
    &--3 {
      margin-left: 2rem;
    }
  }
}
</style>
