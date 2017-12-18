<template>
  <div id="app">
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:add-todo="addTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList, CreateTodo,
  },
  // data function avails data to the template
  data() {
    return {
      todos: [{
        id: 1,
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        id: 2,
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        id: 3,
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }, {
        id: 4,
        title: 'Todo D',
        project: 'Project D',
        done: false,
      }],
    };
  },
  methods: {
    addTodo(title) {
      console.log('*** add todo');
      this.todos.push({
        title,
        done: false,
      });
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
