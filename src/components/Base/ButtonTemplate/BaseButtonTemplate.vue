<template>
  <div class="button-template" :class="{ 'button-template_disabled': disabled }">
    <svg v-if="!!icon" :class="iconClass">
      <use :href="icon"></use>
    </svg>

    <span v-if="$slots['default']" class="button-template__text">
      <slot></slot>
    </span>
  </div>
</template>

<script setup lang="ts">
interface Props {
  icon?: string
  iconClass?: string
  disabled?: boolean
}

withDefaults(defineProps<Props>(), {
  iconClass: 'icon32',
  disabled: false,
})
</script>

<style scoped lang="scss">
.button-template {
  display: flex;
  align-items: center;
  gap: $indent-xm;
  width: max-content;
  padding: $indent-xm $indent-xl;
  border-radius: $border-radius-xm;
  background-color: $accent-light;
  color: $white;
  transition: background-color .3s ease;
  cursor: pointer;

  @media screen and (hover: hover) {
    &:hover:not(&_disabled) {
      background-color: $accent-middle;
    }
  }

  &:active:not(&_disabled) {
    background-color: $accent-dark;
  }

  &_disabled {
    background-color: $gray;
    cursor: default;
  }
}
</style>