<template>
    <div>
      <h2>Todos</h2>
      <input v-model="newTask" @keyup.enter="addTask">
      <button @click="addTask">tambahkan kegiatan</button>
      <div v-for="(task, index) in tasks" :key="index">
        <span :class="{ completed: task.completed }">{{ task.name }}</span>
        <button @click="toggleCompletion(index)">Mark as Done</button>
        <button @click="deleteTask(index)">Delete</button>
      </div>
      <button @click="showIncomplete">tampilkan kegiatan yang belum selesai</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: []
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim()) {
          this.tasks.push({ name: this.newTask, completed: false });
          this.newTask = '';
        }
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
      },
      toggleCompletion(index) {
        this.tasks[index].completed = !this.tasks[index].completed;
      },
      showIncomplete() {
        this.tasks = this.tasks.filter(task => !task.completed);
      }
    }
  }
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }
  </style>
  