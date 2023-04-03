<template>
    <div>
        <h2>add new todo</h2>
        <input type="text" v-model="title" placeholder="Add a new todo">
        <button @click="addTodo">Add</button>
    </div>
</template>

<script>
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
            const response = await fetch('http://localhost:8080/todos', {
                method: 'POST',
                headers: {
                'Content-Type': 'application/json',
                },
                body: JSON.stringify(todo),
            });
            const data = await response.json();
            console.log(data);
            this.$emit('todo-added', data);
            this.title = '';
        },
    },
};
</script>