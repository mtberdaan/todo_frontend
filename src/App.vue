<template>
  <div id="app">
    <TodoList />
    <TodoForm @add-todo="addTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoForm from './components/TodoForm.vue'
import { response } from 'express';

export default {
  name: 'App',
  components: {
   TodoList,
   TodoForm,
  },
  methods: {
    async addTodo(todo) {
      const reponse = await fetch('http://localhost:8080/todos', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(todo),
      });
      const data = await response.json();
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
</style>
