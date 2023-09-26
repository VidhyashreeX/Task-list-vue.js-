<template>
  <li>
    <input type="checkbox" v-model="task.completed" @change="toggleTask" />
    <span :style="{ 'text-decoration': task.completed ? 'line-through' : 'none' }">{{ task.text }}</span>
    <button @click="deleteTask">Delete</button>
  </li>
</template>

<script>
export default {
  props: ['task'],
  methods: {
    deleteTask() {
      this.$emit('deleteTask', this.task.id);
    },
    toggleTask() {
      this.$emit('toggleTask', this.task.id);
    },
  },
};
</script>
