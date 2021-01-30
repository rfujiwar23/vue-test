<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>

import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'App',
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
          title: "Clean Up",
          completed: false
        },
        {
          id: 2,
          title: "Buy stuff",
          completed: true
        },
        {
          id: 3,
          title: "Cook food",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    AddTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  }
}
</script>

<style>
  * {
    box-sizing:border-box;
    margin:0;
    padding:0;
  }

  body {
    font-family:Arial, Helvetica, sans-serif;
    line-height:1.4;
  }

  .btn {
    display:inline-block;
    border:none;
    background:#6d85d4;
    color:#fff;
    text-shadow:1px 1px 3px #000;
    padding:7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }

</style>
