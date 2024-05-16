<template>
    <div>
      <h2>Posts</h2>
      <select v-model="selectedUser" @change="fetchUserPosts">
        <option v-for="user in users" :value="user.id" :key="user.id">{{ user.name }}</option>
      </select>
      <div v-for="(post, index) in userPosts" :key="index">
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        users: [],
        selectedUser: null,
        userPosts: []
      };
    },
    mounted() {
      this.fetchUsers();
    },
    methods: {
      fetchUsers() {
        fetch('https://jsonplaceholder.typicode.com/users')
          .then(response => response.json())
          .then(data => this.users = data)
          .catch(error => console.error('Error fetching users:', error));
      },
      fetchUserPosts() {
        if (this.selectedUser) {
          fetch(`https://jsonplaceholder.typicode.com/posts?userId=${this.selectedUser}`)
            .then(response => response.json())
            .then(data => this.userPosts = data)
            .catch(error => console.error('Error fetching user posts:', error));
        }
      }
    }
  }
  </script>
  
  <style scoped>
  </style>
  