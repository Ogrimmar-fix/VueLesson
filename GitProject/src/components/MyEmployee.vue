<script lang="ts">
export default {
  props: { element: String, id: Number, isChecked: Boolean },
  emits: ['remove', 'cross-out'],
  methods: {
    onCheckboxChange(e) {
      this.$emit('cross-out', this.id, e.target.checked)
    }
  },
  mounted() {
    console.log(this.isChecked, 'isChecked');
  }
}
</script>

<template>
  <div>
    <label>
      <input type="checkbox" class="checkbox" :checked="isChecked" @input="onCheckboxChange" />
      <span :class="{ 'strikethrough': isChecked }" >
        {{ element }}
      </span>
    </label>
  </div>
  <div id="child">
    <button @click="$emit('remove', id)">Удалить</button>
  </div>
</template>

<style>
.strikethrough {
  text-decoration: line-through;
}

.checkbox {
  cursor: pointer;
}
</style>
