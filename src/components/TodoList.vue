<template>
    <div>
        <TodoItem
            v-for="todo of todos" :key="todo.id"
            v-bind:todo="todo"
            v-on:removeTodoItem="removeTodoList"
        />
    </div>
</template>
<script>
    import TodoItem from "@/components/TodoItem";
    export default {
        props: ['todos'],
        components : {
            TodoItem
        },
        methods: {
            removeTodoList(id) {
                this.$emit('removeTodoList', id);
            }
        }
    }
</script>