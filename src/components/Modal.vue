<script setup lang="ts">
import CloseIcon from '../assets/icons/close-icon.svg'

// Пропсы, принимаемые компонентом
const props = defineProps<{
  isOpen: boolean
  title: string
  content: string | VNode
}>()

// События, которые компонент может эмитеть
const emits = defineEmits<{
  close: []
}>()
</script>

<template>
  <div class="modal-container">
    <div class="trigger">
      <CloseIcon class="close-button" @click="emits('close')" @touchstart.passive="() => {}"/>
    </div>

    <h1 class="title">{{ props.title.toUpperCase() }}</h1>

    <div v-if="typeof props.content === 'string'" v-html="props.content"/>

    <component :is="props.content" v-else />

  </div>

</template>

<style scoped lang="scss">
.modal-container {
  position: fixed;
  box-shadow: 1.42px 1.42px 11.39px 2.85px rgba(176, 176, 176, 0.25);
  width: 614px;
  border-radius: 45.57px 45.57px 0 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-height: calc(100dvh - 50px);
  bottom: 0;
  left: 50%;
  translate: -50% 0;

  .trigger {
    flex: none;
    height: 89px;
    padding: 0 33px;
    display: flex;
    align-items: center;
    margin-left: auto;

    .close-button {
      color: #58595B;
      cursor: pointer;
      transition: 0.2s;
      transition-property: scale;

      &:active {
        scale: 0.90;
      }
    }
  }

  .title {
    margin: 0;
    text-align: center;
    max-width: 494px;
    font-weight: bold;
    font-size: 25.63px;

    &::first-line {
      font-weight: normal;
    }
  }

  @media (max-width: 640px) {
    width: calc(100dvw - 20px);
    max-height: calc(100dvh - 20px);
    bottom: 10px;

    .trigger {
      height: 60px;
      padding: 0 23px;

      .close-button {
        width: 32px;
        height: auto;

        &:active {
          scale: 1.2;
        }
      }
    }

    .title {
      font-size: 20px;
    }
  }
}
</style>
