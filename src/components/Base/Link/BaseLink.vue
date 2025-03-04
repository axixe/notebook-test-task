<template>
  <div class="link">
    <slot></slot>
  </div>
</template>

<script setup lang="ts">

</script>

<style scoped lang="scss">
.link {
  width: max-content;
  color: $accent-light;
  transition: color .3s ease;
  cursor: pointer;

  @media screen and (hover: hover) {
    &:hover {
      color: $white;
    }
  }

  &:active {
    color: $white;
  }
}
</style>