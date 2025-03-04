<template>
  <div v-if="!!error || limit" class="input-footer">
    <span class="input-footer__error">{{ error }}</span>
    <span v-if="limit" class="input-footer__letters-counter">{{ inputValueLength }}/{{ limit }}</span>
  </div>
</template>

<script setup lang="ts">
import {computed} from "vue";

interface Props {
  error?: string
  value: string | number
  limit: number
}

const props = withDefaults(defineProps<Props>(), {
  value: '',
})

const inputValueLength = computed(() => {
  return String(props.value).length;
});
</script>

<style scoped lang="scss">
.input-footer {
  display: flex;
  justify-content: space-between;
  padding: $indent-s $indent-xl;

  &__error {
    color: $error;
  }
}
</style>