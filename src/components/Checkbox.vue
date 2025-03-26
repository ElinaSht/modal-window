<script setup lang="ts">
// Отслеживание состояния чекбокса (выбран/не выбран)
const checked = defineModel<boolean>('checked', { required: true })

// Пропс, принимаемый компонентом
const props = defineProps<{
  label: string
}>()
</script>

<template>
  <div class="checkbox-container" @click="checked = !checked" @touchstart.passive="() => {}">

    <div class="icon">
      <div :class="{checked}" class="icon-fill"></div>
    </div>

    <div class="label">{{ props.label.toUpperCase() }}</div>
  </div>
</template>

<style scoped lang="scss">
.checkbox-container {
  display: flex;
  gap: 32px;
  cursor: pointer;
  align-items: center;

  .icon {
    width: 41px;
    height: 41px;
    border: 3.42px solid #58595B;
    border-radius: 6.83px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-shrink: 0;

    .icon-fill {
      width: 27px;
      height: 27px;
      background-color: transparent;
      border-radius: 100%;
      scale: 0.5;
      transition: 0.2s;
      transition-property: background-color, border-radius, scale;
      will-change: background-color, border-radius, scale;


      &.checked {
        background-color: #CD10FF;
        border-radius: 3.42px;
        scale: 1;
      }
    }
  }

  @media (max-width: 640px) {
    gap: 16px;

    .icon {
      width: 30px;
      height: 30px;

      .icon-fill {
        width: 20px;
        height: 20px;
      }
    }

  }
}

</style>
