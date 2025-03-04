<template>
  <BaseInput v-model="inputValue" :type="isShowInputContent ? 'text' : 'password'">
    <template #icon>
      <svg @click="editInputContentDisplaying" class="icon20">
        <use :href="`src/assets/images/icons/icon-eye_${ isShowInputContent ? 'open' : 'close' }.svg#icon`"></use>
      </svg>
    </template>
  </BaseInput>
</template>

<script setup lang="ts">
import BaseInput from "@/components/Base/Inputs/BaseInput.vue";
import { ref } from "vue";

const inputValue = defineModel('modelValue')
const isShowInputContent = ref(false)

const editInputContentDisplaying = () => {
  isShowInputContent.value = !isShowInputContent.value
}
</script>

<style scoped lang="scss"></style>