<script setup lang="ts">
import Modal from '@/components/Modal.vue'
import Content from '@/components/Content.vue'
import { onClickOutside } from '@vueuse/core'

// Переменная для хранения номера заказа
const order = ref<string>('У00017711')
// Переменная для хранения заголовка модального окна
const title = `Отказаться от выполнения заказа № ${ order.value }`

// Переменная, определяющая, открыто ли модальное окно
const isOpen = ref<boolean>(true)

// Функция закрытия модального окна
function onClose() {
  isOpen.value = false
}

// Ссылка на корневой элемент
const rootRef = shallowRef<HTMLElement>()
// Хук для закрытия модального окна, при клике на область вне него
onClickOutside(rootRef, () => isOpen.value = false)
</script>
<template>
  <div class="app">
      <Modal
        v-if="isOpen"
        ref="rootRef"
        :title
        :content="h(Content)"
        :is-open="isOpen"
        class="modal-window"
        @close="onClose"
      />
  </div>
</template>

<style scoped lang="scss">
.app {
  .modal-window {
    flex: 1;
  }
}
</style>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,300..900;1,300..900&display=swap');

html {
  padding: env(safe-area-inset-top) env(safe-area-inset-right) env(safe-area-inset-bottom) env(safe-area-inset-left);
}

html, body, #app {
  width: 100%;
  height: 100%;
  overflow: auto;
  touch-action: manipulation;
  user-select: none;
}

body {
  margin: 0;
  font-family: "Rubik", sans-serif;
  font-size: 25.63px;
  line-height: 28.5px;
  color: #151A22;

  ::-webkit-scrollbar {
    width: 8px;
  }

  ::-webkit-scrollbar-thumb {
    background: #D9D9D9;
  }
}

* {
  box-sizing: border-box;
}
</style>
