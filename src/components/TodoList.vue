<template>
    <div>
        <h2>current todos</h2>
        <ul id="list">
            <li v-for="todo in todos" :key="todo.id">
                {{ todo.title }}
            </li>
        </ul>
    </div>
</template>
  
<script>
import axios from 'axios';

export default {
    data() {
        return {
            todos: [],
        };
    },
    created() {
        this.getTodos();
    },
    methods: {
        async getTodos() {
            try {
                const response = await axios.get('http://localhost:8080/todos');
                this.todos = response.data;
            } catch (error) {
                console.error(error);
            }
        },
    },
};
</script>
