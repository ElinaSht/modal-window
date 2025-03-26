<script setup lang="ts">
import Button from '@/components/Button.vue'
import ru from "../locales/ru.json"

// Реактивный массив, хранящий состояние выбран/не выбран (true/false) для каждого элемента из ru.reasons
const checked = ref<boolean[]>(ru.reasons.map(() => false))
</script>

<template>
  <div class="content-container">
    <h1 class="header">{{ ru.header.toUpperCase() }}</h1>

    <div class="list">
      <div v-for="(reason, i) in ru.reasons" :key="i">
        <Checkbox v-model:checked="checked[i]" :label="reason"/>
      </div>
    </div>

    <Button label="Отправить" class="button" />

  </div>
</template>

<style scoped lang="scss">
.content-container {
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
  overflow: hidden;

  .header {
    margin: 0 0 55px 0;
    max-width: 522px;
    text-align: center;
    font-weight: bold;
    color: #343330;
    font-size: 25.63px;
  }

  .list {
    display: flex;
    flex-direction: column;
    gap: 45px;
    overflow: auto;
    width: 100%;
  }

  @media (max-width: 640px) {
    margin-top: 20px;
    font-size: 20px;
    padding: 0 10px;

    .header {
      margin-bottom: 30px;
    }

    .list {
      gap: 20px;
    }
  }
}
</style>
