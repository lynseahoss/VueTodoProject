<template>

  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/layout/Header.vue'
import Todos from './components/Todos.vue';
import AddTodo from './components/AddTodo';
export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
    
  },
  data(){
    return {
     todos: []
    }
    },
    methods: {
      deleteTodo(id){
        this.todos = this.todos.filter(todo => todo.id !== id)
      },
      addTodo(newTodo){
        this.todos = [...this.todos, newTodo]
      },
      created(){
        axios.get('https://jsonplaceholder.typicode.com/todos')
        .then(res=> this.todos = res.data)
        .catch(err=>console.log(err))
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
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn{
  display: inline-block;
  border: none;
  background: #f021e5;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
</style>
