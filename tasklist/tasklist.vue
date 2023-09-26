<template>
  <div>
    <h1>Task List</h1>
    <TaskForm @addTask="addTask" />
    <div>
      <label>Show: </label>
      <button @click="filterTasks('all')">All</button>
      <button @click="filterTasks('completed')">Completed</button>
      <button @click="filterTasks('incomplete')">Incomplete</button>
    </div>
    <ul>
      <TaskItem v-for="task in filteredTasks" :key="task.id" :task="task" @deleteTask="deleteTask" @toggleTask="toggleTask" />
    </ul>
  </div>
</template>

<script>
import TaskForm from './TaskForm.vue';
import TaskItem from './TaskItem.vue';

export default {
  components: {
    TaskForm,
    TaskItem,
  },
  data() {
    return {
      tasks: [
        { id: 1, text: 'Task 1', completed: false },
        { id: 2, text: 'Task 2', completed: true },
        // ... add more tasks as needed
      ],
      filter: 'all',
    };
  },
  computed: {
    filteredTasks() {
      if (this.filter === 'all') {
        return this.tasks;
      } else if (this.filter === 'completed') {
        return this.tasks.filter(task => task.completed);
      } else if (this.filter === 'incomplete') {
        return this.tasks.filter(task => !task.completed);
      }
      return this.tasks;
    },
  },
  methods: {
    addTask(task) {
      this.tasks.push(task);
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter(task => task.id !== taskId);
    },
    toggleTask(taskId) {
      this.tasks = this.tasks.map(task => (task.id === taskId ? { ...task, completed: !task.completed } : task));
    },
    filterTasks(type) {
      this.filter = type;
    },
  },
};
</script>
