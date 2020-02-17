<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" v-on:edit-todo="editTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>
<script>
import Todos from './components/Todos';
import AddTodo from './components/AddToDo.vue';


export default {
  name: 'app',
  components: {
    Todos,
    AddTodo,
  },

  data() {
    return {
      todos: []
}
  },

 methods: {
    addTodo(newTodoObj) {
      this.todos = [...this.todos, newTodoObj];
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    },
    editTodo(todoTitle){
        this.todos = this.todos.edit(todo => todo.title == todoTitle);
    }


  }
}
</script>
<style>
</style>
