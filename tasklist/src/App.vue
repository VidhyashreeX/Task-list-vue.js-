<template>
  <div class="centered-content">
    <h1>Task List</h1>
    <h3>Stay productive and complete your tasks!</h3>
    <h3>This project is done by Vidhyashree</h3>

    <input type="text" v-model="newTask" placeholder="Add a new task" @keyup.enter="addTask" />

    <ul>
      <li v-for="task in filteredTasks" :key="task.id">
        <input type="checkbox" v-model="task.completed" />
        {{ task.text }}
        <button @click="removeTask(task.id)">Delete</button>
      </li>
    </ul>

    <!-- Task filter buttons -->
    <div>
      <label>STATUS: </label>
      <button @click="filterTasks('all')">All</button>
      <button @click="filterTasks('completed')">Completed</button>
      <button @click="filterTasks('incomplete')">Incomplete</button>
    </div>
  </div>
</template>

<style scoped>
/* ... your existing styles ... */

/* Add animation styles */
.animated-button {
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
}

.animated-button:hover {
  background: #000;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 0, 0, 0.5), 0 0 30px rgba(0, 0, 0, 0.5);
}
</style>


<script>
export default {
  data() {
    return {
      tasks: [
        { id: 1, text: 'Complete the project report for the team meeting.', completed: false },
        { id: 2, text: 'Manage medications and prescriptions.', completed: true }
        
      ],
      newTask: '',
      filter: 'all'
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
    }
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.tasks.push({ id: this.tasks.length + 1, text: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    removeTask(taskId) {
      this.tasks = this.tasks.filter(task => task.id !== taskId);
    },
    filterTasks(type) {
      this.filter = type;
    }
  }
};
</script>


<style>
/* Global styles */
body, html {
  margin: 0;
  padding: 0;
  height: 100%;
  background-color: #242424;
  background: linear-gradient(to right, #ffafbd, #ffc3a0);
}

.button-completed,
.button-incomplete {
  background: #03e9f4;
  color: #fff;
  border-radius: 5px;
  box-shadow: 0 0 5px #03e9f4 !important;
}

.button-completed:hover,
.button-incomplete:hover {
  background: #03e9f4 !important;
  color: #fff !important;
  border-radius: 5px !important;
  box-shadow: 0 0 5px #03e9f4, 0 0 25px #03e9f4, 0 0 50px #03e9f4, 0 0 100px #036ff4 !important;
}
</style>

<style scoped>
/* Existing styles */

/* Add styles for glowing effect */
.button-completed:hover {
  background: #000;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 0, 0, 0.5), 0 0 30px rgba(0, 0, 0, 0.5);
}

.button-all:hover {
  background: #000;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 0, 0, 0.5), 0 0 30px rgba(0, 0, 0, 0.5);
}

.button-incomplete:hover {
  background: #000;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 0, 0, 0.5), 0 0 30px rgba(0, 0, 0, 0.5);
}
</style>





<style scoped>
/* Add this style to increase button size */
button {
  padding: 15px 15px; 
  font-size: 0.5em; 
}
</style>

<style scoped>

input[type="text"] {
  height: 50px; 
  font-size: 1.0em; 
}
</style>


<style scoped>
.centered-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  text-align: center;
}
</style>
