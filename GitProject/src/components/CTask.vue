<script setup lang="ts">
defineProps({
  name: String,
  index: Number,
})
const emit = defineEmits(['clicker', 'add', 'remove'])
</script>

<template>
  <ul class="parent">
    <li @click="emit('clicker', name, index)">{{ name }}</li>
    <button @click="emit('remove', index)">Удалить</button>
  </ul>
</template>

<style>
.strikethrough {
  text-decoration: line-through;
}

li {
  color: black;
  cursor: pointer;
}
textarea {
  color: black;
}
li:hover {
  background: #f0f0f0;
}
.parent {
  display: flex;

  justify-content: space-between;
}
</style>
