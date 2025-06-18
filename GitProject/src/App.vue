<script lang="ts">
import MyEmployee from './components/MyEmployee.vue'

export default {
  components: {
    MyEmployee,
  },
  data() {
    return {
      selectedText: '',
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
    clickRecord(text: string) {
      this.selectedText = text
    },
    applyChange() {
      this.listRecords.name = this.selectedText
    },
  },
}
</script>

<template>
  <div class="row">
    <div class="row-child">
      <MyEmployee
        v-for="record in listRecords"
        :key="record.id"
        :name="record.name"
        @clicker="clickRecord(record.name)"
      />
    </div>
    <div>
      <textarea v-model="selectedText" @keyup.enter="applyChange" class="area"></textarea>
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
