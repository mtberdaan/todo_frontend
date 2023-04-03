<template>
    <div>
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
        addTodo() {
            const todo = {
                title: this.title,
            };
            this.$emit('add-todo', todo);
            this.title = '';
        },
    },
};
</script>