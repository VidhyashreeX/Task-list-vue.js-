<template>
  <div>
    <input v-model="taskText" placeholder="Add a new task" @keyup.enter="addTask" />
    <button @click="addTask">Add Task</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      taskText: '',
    };
  },
  methods: {
    addTask() {
      const trimmedText = this.taskText.trim();
      if (trimmedText !== '') {
        const newTask = { id: Date.now(), text: trimmedText, completed: false };
        this.$emit('addTask', newTask);
        this.taskText = '';
      }
    },
  },
};
</script>