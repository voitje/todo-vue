<template>
  <div id="app">
    <todo-list text=""/>
    <div>
      <input class="input" type="text" @change="handleChange"/>
      <button class="btn-save" type="button" @click="addTodo">Сохранить</button>
    </div>
    <TodoList
      v-bind:todos="todos"
      @removeTodoList="removeTodo"
    />
  </div>
</template>

<script>
  import TodoList from "@/components/TodoList";
  export default {
    name: 'app',
    data() {
      return {
        todos: [],
        text: ''
      }
    },
    components: {
      TodoList
    },
    mounted() {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
              .then(response => response.json())
              .then(json => {
                this.todos = json
              })
    },
    methods: {
      handleChange() {
        this.todoName = event.target.value;
      },
      addTodo() {
        let newTodo = {
          id: Date.now(),
          title: this.todoName,
          completed: false,
        };
        this.todos.push(newTodo);
      },
      removeTodo(id) {
        this.todos = this.todos.filter(t => t.id !== id);
      },
    }
  }
</script>

<style>
  #app {
    font-family: "Fira Sans", sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .btn-save {
    width: 105px;
  }
  .input {
    width: 105px;
  }
</style>
