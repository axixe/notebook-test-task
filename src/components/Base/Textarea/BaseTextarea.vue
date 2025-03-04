<template>
  <div class="textarea">
    <label class="textarea__wrapper">
      <span v-if="!!label" class="textarea__label">{{ label }}</span>

      <textarea
        v-model="inputValue"
        class="textarea__element"
        :placeholder="label"
        :disabled="disabled"
        :maxlength="maxlength"
      />
    </label>

    <BaseInputFooter :error="error" :value="inputValue" :limit="maxlength" />
  </div>
</template>

<script setup lang="ts">
import BaseInputFooter from "@/components/Base/Inputs/BaseInputFooter.vue";

interface Props {
  error?: string
  label?: string
  disabled?: boolean
  maxlength?: number
}

withDefaults(defineProps<Props>(), {
  disabled: false,
})

const inputValue = defineModel<string | number>('modelValue', { default: '' })
</script>

<style scoped lang="scss">
.textarea {
  &__label {
    display: block;
    padding: 0 $indent-xl $indent-s;
    color: $gray;
  }

  &__element {
    display: flex;
    align-items: center;
    width: 100%;
    height: 244px;
    padding: $indent-m $indent-xl;
    border: 1px solid transparent;
    border-radius: $border-radius-m;
    background-color: $white;
    color: $base;
    transition: border-color .3s ease;

    &:hover,
    &:focus {
      border-color: $accent-light;
    }

    @media screen and (max-width: $laptop) {
      height: 168px;
    }
  }
}
</style>