<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>

    <div v-if="todos && todos.length">
    <todo 
      v-on:delete-todo="deleteTodo" 
      v-on:complete-todo="completeTodo" 
    	v-for="(todo, index) in todos" 
    	v-bind:todo="todo" 
    	v-bind:index="index" 
    	:key="todo.id">
    </todo>
    </div>

    <ul v-if="errors && errors.length">
    <li v-for="error of errors">
      {{error.message}}
    </li>
  	</ul>

  </div>
</template>

<script type = "text/javascript" >
	import axios from 'axios';
	import Todo from './Todo';

	export default {
    props: ['todos'],
	  components: { Todo },
	  methods: {
	    deleteTodo(todo) {
	      console.log('*** delete in the list');
	      const todoIndex = this.todos.indexOf(todo);
	      this.todos.splice(todoIndex, 1);
	    },
      completeTodo(todo) {
        console.log('*** complete in the list');
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].completed = true;
      },
	  },
  	  data() {
        return {
          // todos: [],
          errors: []
        }
      },

      // Fetches todos when the component is created.
      created() {
        console.log('creating list object');
        axios.get(`http://jsonplaceholder.typicode.com/todos`)
          .then(response => {
            // JSON responses are automatically parsed.
            console.log(response.data);
            this.todos.push.apply(this.todos, response.data.slice(1, 5));
            //this.todos = response.data.slice(1, 5);
          })
          .catch(e => {
            this.errors.push(e)
          })
      }

 	}
</script>