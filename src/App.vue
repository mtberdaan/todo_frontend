<template>
  <div id="app">
    <h1>Todos</h1>
    <TodoForm @todo-added="handleTodoAdded" />
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoForm from './components/TodoForm.vue'

export default {
  name: 'App',
  components: {
   TodoList,
   TodoForm,
  },
  methods: {
    handleTodoAdded(data) {
      console.log(data);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#list {
  list-style-type: none;
}
</style>
