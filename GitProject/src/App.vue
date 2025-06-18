<script lang="ts">
import MyEmployee from './components/MyEmployee.vue'

export default {
  components: {
    MyEmployee,
  },
  data() {
    return {
      currentId: 2,
      nameBox: ['One', 'Two', 'Three', 'Four', 'Five', 'Six', 'Seven', 'Eight', 'Nine', 'Ten'],
      rowsDelo: [
        {
          id: 1,
          name: 'DeloOne',
          isRemoved: true,
        },
        {
          id: 2,
          name: 'DeloTwo',
          isRemoved: false,
        },
      ],
    }
  },
  methods: {
    crossOut(id: number, value: boolean) {
      const element = this.rowsDelo.find(x => x.id === id);
      if (!element) {
        return;
      }

      element.isRemoved = value;
      console.log(this.rowsDelo, 'this.rowsDelo');
    },
    remove(id: number) {
      this.rowsDelo = this.rowsDelo.filter((elem) => {
        return elem.id !== id
      })
    },
    addLine() {
      const newIndex = this.currentId++;
      let newName = 'Delo ';
      const numberStringValue = this.nameBox[newIndex];
      console.log(newIndex, 'newIndex');
      newName += numberStringValue ? numberStringValue : newIndex;

      this.rowsDelo.push({
        id: newIndex,
        name: newName,
        isRemoved: false,
      })
    },
  },
}
</script>

<template>
  123
  <MyEmployee
    class="parent"
    v-for="elem in rowsDelo"
    :key="elem.id"
    :element="elem.name"
    :id="elem.id"
    :isChecked="elem.isRemoved"
    @remove="remove"
    @cross-out="crossOut"
  />
  <button @click="addLine">Добавить</button>
</template>
<style>
.parent {
  margin: auto;
}
</style>
