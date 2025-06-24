<script setup lang="ts">
import { ref } from 'vue'
import CTask from './components/CTask.vue'

// Refs
const selectedItem = ref({})
const listRecords = ref([
  {
    id: 1,
    name: 'Забрать ребенка из школы.',
  },
  {
    id: 2,
    name: 'Купить лекарства.',
  },
  {
    id: 3,
    name: 'Записаться к врачу.',
  },
  {
    id: 4,
    name: 'Приготовить обед',
  },
])

// Functions
function clickRecord(record: object) {
  selectedItem.value = { ...record }
}

function addText() {
  const result = listRecords.value.find((element) => element.id === selectedItem.value.id)
  if (!result) {
    return
  }

  result.name = selectedItem.value.name
}

function addItem() {
  listRecords.value.push({ id: 5, name: '' })
}
function removeItem(element) {
  console.log(selectedItem.value.id, 'selectedItem.value.id')
  listRecords.value = listRecords.value.filter(() => {
    return selectedItem.value.id !== element.id
  })
  console.log(element.id, 'element.id')
}
</script>

<template>
  <div class="row">
    <div class="row-child">
      <CTask
        v-for="record in listRecords"
        :index="record.id"
        :key="record.id"
        :name="record.name"
        @clicker="clickRecord(record)"
        @remove="removeItem(record)"
      />
      <button @click="addItem">Добавить задачу</button>
    </div>
    <div>
      <textarea v-model="selectedItem.name" class="area"></textarea>

      <button @click="addText">Добавить</button>
      <button @click="selectedItem.name = ''">Очистить</button>
    </div>
  </div>
</template>

<style>
.row {
  display: flex;

  justify-content: space-between;
}
.row-child {
  margin-right: 10px;
}
.area {
  margin-right: 10px;
}
</style>
