<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo';
import Todos from './components/Todos';
import Header from './components/layout/header';

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "To-Do One",
          completed: false
        },
        {
          id: 2,
          title: "To-Do Two",
          completed: false
        },
        {
          id: 3,
          title: "To-Do Three",
          completed: false
        },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  } 
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
