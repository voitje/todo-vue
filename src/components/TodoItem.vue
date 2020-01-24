<template>
    <div class="name-todo">
        <span v-bind:class="{done: todo.completed}">
            <input class="checkbox" type="checkbox" v-on:change="todo.completed = !todo.completed"/>
            {{ todo.title }}
        </span>
        <button class="btn-rem" v-on:click="$emit('removeTodoItem', todo.id)">&times;</button>
    </div>
</template>

<script type="text/javascript">

    export default {
        props: {
            todo: {
                type: Object,
                required: true
            }
        }
    }
</script>

<style scoped>
    .name-todo {
        display: flex;
        justify-content: space-between;
        margin-top: 10px;
        align-items: center;
        width: 150px;
        height: 50px;
        border: 1px solid #cccccc;
        padding: .4rem 2rem ;
    }
    .done {
        text-decoration: line-through;
    }
    .btn-rem {
        border: none;
        background: red;
        border-radius: 50%;
        color: #fff;
        font-weight: bold;
        outline: none;
        cursor: pointer;
    }
    .checkbox {
        cursor: pointer;
        color: #444;
        background-repeat: no-repeat;
    }
</style>