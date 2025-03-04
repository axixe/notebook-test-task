<template>
  <div class="input">
    <label class="input__wrapper">
      <span v-if="!!label" class="input__label">{{ label }}</span>

      <div class="input__element-wrapper">
        <input
          v-model="inputValue"
          :type="type"
          class="input__element"
          :placeholder="label"
          :disabled="disabled"
          :maxlength="maxlength"
        />

        <div class="input__icon">
          <slot name="icon"></slot>
        </div>
      </div>
    </label>

    <BaseInputFooter :error="error" :value="inputValue" :limit="maxlength" />
  </div>
</template>

<script setup lang="ts">
import BaseInputFooter from '@/components/Base/Inputs/BaseInputFooter.vue'

interface Props {
  error?: string
  label?: string
  disabled?: boolean
  maxlength?: number
  type?: string
}

withDefaults(defineProps<Props>(), {
  disabled: false,
  type: 'text'
})

const inputValue = defineModel<string | number>('modelValue', { default: '' })
</script>

<style scoped lang="scss">
.input {
  &__label {
    display: block;
    padding: 0 $indent-xl $indent-s;
    color: $gray;
  }

  &__element-wrapper {
    display: flex;
    align-items: center;
    border: 1px solid transparent;
    border-radius: $border-radius-m;
    background-color: $white;
    transition: border-color .3s ease;

    &:hover,
    &:focus-within {
      border-color: $accent-light;
    }
  }

  &__element {
    width: 100%;
    padding: $indent-xl $indent-xm $indent-xl $indent-xl;
    background-color: transparent;
    color: $base;
  }

  &__icon {
    display: flex;
    align-items: center;
    margin-right: $indent-xl;
    cursor: pointer;
  }
}
</style>