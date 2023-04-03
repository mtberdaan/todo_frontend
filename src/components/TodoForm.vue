<template>
    <div>
        <h2>add new todo</h2>
        <input type="text" v-model="title" placeholder="Add a new todo">
        <button @click="addTodo">Add</button>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            title: '',
        };
    },
    methods: {
        async addTodo() {
            const todo = {
                title: this.title,
            };
            const response = await axios.post('http://localhost:8080/todos', todo);
            const data = await response.data;
            console.log(data);
            this.$emit('todo-added', data);
            this.title = '';
        },
    },
};
</script>