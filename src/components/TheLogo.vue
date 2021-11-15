<template>
  <div class="logo">Vue<span class="logo__highlight">Calculator</span></div>
</template>

<style lang="scss" scoped>
@use "../assets/styles/index.scss" as *;
.logo {
  color: $color-text-2;
  &__highlight {
    color: $color-keys-6;
  }
}
</style>
