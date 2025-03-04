<template>
  <button type="button" :disabled="disabled">
    <BaseButtonTemplate :icon="icon" :icon-class="iconClass" :disabled="disabled">
      <slot></slot>
    </BaseButtonTemplate>
  </button>
</template>

<script setup lang="ts">
import BaseButtonTemplate from "@/components/Base/ButtonTemplate/BaseButtonTemplate.vue";

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

<style scoped lang="scss"></style>