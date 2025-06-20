<script lang="ts">
export default {
  props: { name: String, index: Number },
  emits: ['clicker'],
  methods: {},
}
</script>

<template>
  <ul>
    <li @click="$emit('clicker', name, index)">{{ name }}</li>
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
