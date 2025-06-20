<script lang="ts">
import MyEmployee from './components/MyEmployee.vue'

export default {
  components: {
    MyEmployee,
  },
  data() {
    return {
      selectedText: '',
      selectedItem: 0,
      listRecords: [
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
      ],
    }
  },
  methods: {
    clickRecord(text: string, id: number) {
      this.selectedText = text
      this.selectedItem = id
    },
    addText() {
      const result = this.listRecords.find((element) => element.id === this.selectedItem)
      result.name = this.selectedText
    },
  },
}
</script>

<template>
  <div class="row">
    <div class="row-child">
      <MyEmployee
        v-for="record in listRecords"
        :index="record.id"
        :key="record.id"
        :name="record.name"
        @clicker="clickRecord(record.name, record.id)"
      />
    </div>
    <div>
      <textarea v-model="selectedText" class="area"></textarea>
      <button @click="addText">Добавить</button>
      <button @click="selectedText = ''">Очистить</button>
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
