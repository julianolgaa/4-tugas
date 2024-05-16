<template>
  <div id="app">
    <header>
      <h1>Daily Activity</h1>
      <nav>
        <button @click="currentView = 'todos'">Todos</button>
        <button @click="currentView = 'posts'">Post</button>
      </nav>
    </header>

    <div v-if="currentView === 'todos'">
      <TodosComponent />
    </div>
    <div v-else-if="currentView === 'posts'">
      <PostsComponent />
    </div>
  </div>
</template>

<script>
import TodosComponent from './components/TodosComponent.vue';
import PostsComponent from './components/PostsComponent.vue';

export default {
  components: {
    TodosComponent,
    PostsComponent
  },
  data() {
    return {
      currentView: 'todos'
    };
  }
}
</script>

<style scoped>
</style>
