<template>
  <div class="note">
    <h4 class="note__title">Заголовок</h4>

    <p class="note__content">А также явные признаки победы институционализации могут быть объединены в целые кластеры себе подобных.</p>

    <button class="note__button-delete-wrapper">
      <svg class="icon16">
        <use :href="'src/assets/images/icons/icon-close.svg#icon'"></use>
      </svg>

      <span class="note__button-delete-text">Удалить</span>
    </button>
  </div>
</template>

<script setup lang="ts">

</script>

<style scoped lang="scss">
.note {
  width: max-content;
  max-width: 480px;
  padding: $indent-l $indent-xl $indent-s;
  border-radius: $border-radius-s;
  background-color: $accent-light;

  &__title {
    position: relative;
    padding-bottom: $indent-l;

    &::after {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 1px;
      background-color: $accent;
    }
  }

  &__content {
    padding: $indent-l 0 $indent-2xl;
  }

  &__button-delete-wrapper {
    display: flex;
    align-items: center;
    gap: $indent-xm;
    margin-left: auto;
  }

  &__button-delete-text {
    @include text-normal;
    color: $white;
  }
}
</style>