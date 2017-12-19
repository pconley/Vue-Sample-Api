<template>
  <div id="app">
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:create-todo="addTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

import TodoService from './services/TodoService';

export default {
  name: 'app',
  components: {
    TodoList, CreateTodo,
  },
  // data function avails data to the template
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(object) {
      console.log('*** add todo', this.todos.length, object);
      object.id = 100+this.todos.length;
      this.todos.push(object);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
