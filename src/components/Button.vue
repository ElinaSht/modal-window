<script setup lang="ts">
// Пропс, принимаемый компонентом
const props = defineProps<{
  label: string
}>()
</script>

<template>
<div class="button-container">
  <div class="content" @touchstart.passive="() => {}">
    {{ props.label.toUpperCase() }}
  </div>
</div>
</template>

<style scoped lang="scss">
.button-container {
  padding: 40px 51px;
  width: 100%;
  background: white;
  cursor: pointer;

  .content {
    border: 1.42px solid #CD10FF;
    border-radius: 11.39px;
    font-size: 19.94px;
    padding: 23px;
    text-align: center;
    color: #000000;
    background-color: transparent;
    transition: 0.2s;
    transition-property: background-color, scale;

    &:hover {
      background-color: rgba(205, 16, 255, 0.10);
    }

    &:active {
      scale: 0.98;
    }
  }

  @media (max-width: 640px) {
    padding: 20px 25px;

    .content {
      padding: 12px;

      &:hover {
        background-color: transparent;
      }
    }
  }
}

</style>
