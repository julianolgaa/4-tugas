<template>
    <div>
      <span :class="{ completed: task.completed }">{{ task.name }}</span>
      <button @click="toggleCompletion">Mark as Done</button>
      <button @click="deleteTask">Delete</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      task: Object,
      index: Number
    },
    methods: {
      toggleCompletion() {
        this.$emit('toggle-completion', this.index);
      },
      deleteTask() {
        this.$emit('delete-task', this.index);
      }
    }
  }
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }
  </style>
  