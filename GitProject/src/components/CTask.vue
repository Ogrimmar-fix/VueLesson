<script setup lang="ts">
  defineProps({
    name: String,
    index: Number
  });
  const emit = defineEmits(['clicker', 'add'])
</script>

<template>
  <ul>
    <li @click="emit('clicker', name, index)">{{ name }}</li>
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
</style>
